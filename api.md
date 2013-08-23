Generate tokens:

    require 'securerandom'

    SecureRandom.hex(n=36)
    => "d9524df01da5ee187d94dc3ae43ac06bbd76157840620925d9a39876e1d81dae3c15cde0"

Restrict access:

    before_filter :restrict_access

    private
      
      # params[:token]
      def restrict_access
        api_key = ApiKey.find_by_token(params[:token])
        head :unauthorized unless api_key
      end

      # http header
      def authenticate
        authenticate_or_request_with_http_token do |token, options|
          ApiKey.exists?(token: token)
        end
      end

      curl http://localhost:3000/api/products -H 'Authorization: Token token="afbadb4ff8485c0adcba486b4ca90cc4"'

rubify strings

    class Hash

      # Converts all of the keys to strings, optionally formatting key name
      def rubyify_keys!
        keys.each{|k|
          v = delete(k)
          new_key = k.to_s.underscore
          self[new_key] = v
          v.rubyify_keys! if v.is_a?(Hash)
          v.each{|p| p.rubyify_keys! if p.is_a?(Hash)} if v.is_a?(Array)
        }
        self
      end
      
    end

Good reads:

[What makes a good API wrapper?](http://wynnnetherland.com/journal/what-makes-a-good-api-wrapper)