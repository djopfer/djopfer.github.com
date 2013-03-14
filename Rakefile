require 'bundler'
Bundler.require

desc "generate to _site"
task :generate do
  system "jekyll"
end

desc "preview at http://localhost:4000"
task :preview do
  system "jekyll --server --auto"
end

desc "deploy to github"
task :deploy => [:generate] do
  origin = `git config --get remote.origin.url`.strip

  cd "_site" do
    system "git init"
    system "git remote add origin #{origin}"
    system "git add ."
    system "git add -u"
    system "git commit -m \"Site updated at #{Time.now.utc}\""
    system "git push origin master --force"
  end
end

