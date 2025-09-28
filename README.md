# Ruby-Jekyll local setup in MacOs
## ⬇️ Install Ruby + Bundler + Jekyll

1. Use a Ruby version manager to isolate Ruby and gems from the system version
```
brew install rbenv ruby-build
rbenv install 3.4.6 # example: install Ruby 3.4.6
rbenv global 3.4.6
gem install bundler jekyll
```

2. Add Ruby to shell path:  
```
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

3. Check versions:
```
ruby -v
jekyll -v
bundler -v
```

## 🔧 To reset ruby version in user environment
rbenv uses .ruby-version files in a directory to decide which Ruby to use.  
- If you’re in /Users/smfirdaus and you see Ruby 3.4.6, it probably means there’s a file .ruby-version inside that directory with 3.4.6 written in it.  
- When you cd into /Users, there’s no .ruby-version, so rbenv falls back to the global Ruby version you set with rbenv global.  

1.	Check if there’s a .ruby-version file:  
`ls -a /Users/smfirdaus | grep ruby-version`  

2.	If it exists and you don’t want a local override in your home directory:  
`rm /Users/smfirdaus/.ruby-version`

3.	Now when you cd into /Users/smfirdaus, it will no longer force Ruby 3.4.6 — it will follow whatever you set globally.

## 🌍 Setting Ruby for a new project repo
When you git clone and cd into a project:

1.	Pick the Ruby you want, e.g.:  
`rbenv install 3.3.0   # if not installed yet`

2.	Inside the repo folder, set the local version:  
`cd my-repo`
`rbenv local 3.3.0`
This creates a .ruby-version file in that repo.

3. Confirm it’s working:  
`ruby -v`

##	👉 Quick tip:
	•	rbenv versions → shows all installed Rubies
	•	rbenv global <version> → set default system-wide version
	•	rbenv local <version> → set version only for current project (creates .ruby-version)
	•	rbenv shell <version> → temporary version for just that shell session
