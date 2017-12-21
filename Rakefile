# http://ixti.net/software/2013/01/28/using-jekyll-plugins-on-github-pages.html

require "jekyll"

REPO = "kanglib.github.io"

task :generate do
    Jekyll::Site.new(Jekyll.configuration).process
end

task :publish => :generate do
    repo = "#{Dir.home}/#{REPO}"
    rm_rf Dir.glob("#{repo}/*")
    cp_r "_site/.", repo

    pwd = Dir.pwd
    Dir.chdir repo

    system "git add ."
    system "git commit -m '#{Time.now}'"
    system "git push origin master -f"

    Dir.chdir pwd
end
