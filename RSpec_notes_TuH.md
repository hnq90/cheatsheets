**Listing 5.16** Additions to .autotest needed to run integration tests with Autotest on OS X.


**Model settings:**

	validates :email, :presence => true,
		:format => { :with => email_regex },
		:uniqueness => { :case_sensitive => false}

**Migration to add email uniqueness:**

	add_index :users, :email, :unique => true



	



		end
		
		it "should reject duplicate email addresses" do



				User.new(@attr.merge(:password_confirmation => "invalid")).should_not be_valid
				User.new(hash).should_not be_valid

				User.new(hash).should_not be_valid





	# Automatically create the virtual attribute 'password_confirmation'.
	validates :password, :presence => true,





