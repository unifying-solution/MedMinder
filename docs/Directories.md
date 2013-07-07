# Directory Structure

* `MedMinder` - Project root
	* `docs` - Project documentation, requirements docs, database schemas
	* `fuel` - FuelPHP application framework and classes
		* `app` - Application classes
			* `cache` - Working directory for FuelPHP cache
			* `classes` - Application classes
				* `controller` - Controller classes
				* `model` - Model classes
				* `view` - ViewModel classes
			* `config` - Application configuration
				* `development` - Environment specific configuration for development
				* `production` - Environment specific configuration for production
				* `testing` - Environment specific configuration for testing
				* `staging` - Environment specific configuration for staging **Not Used**
			* `lang` - Translations and internationalization
			* `logs` - Applications logs
			* `migrations` - Database migration and versioning handlers
			* `modules` - Groups of related MVC classes
			* `tasks` - Classes that are run through the command line or via cron
			* `tests` - Unit tests and testing code
			* `tmp` - Working directory for temporary storage
			* `vendor` - Third-party dependencies installed using [http://getcomposer.org](Composer) 
			* `views` - View templates (PHP or Markdown)
		* `core` - FuelPHP core framework (provided by Git submodule)
		* `packages` - Extra FuelPHP packages (provided by Git submodules)
	* `public` - Web server root
		* `assets` - Static assets
			* `css` - Style sheets
			* `js` - JavaScript sources
			* `img` - Image resources
		* `index.php` - Application boot strap and launchder

