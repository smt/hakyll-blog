require 'fileutils'

def ensure_index(directory, file_404)
    index_path = File.join(directory, "index.html")
    if not File.exists?(index_path)
        FileUtils.copy(file_404, index_path)
    end

    Dir.foreach(directory) do |item|
        new_path = File.join(directory, item)
        next if item == '.' or item == '..' or not File.directory?(new_path)
        ensure_index(new_path, file_404)
    end
end

task :build do
  # Build Hakyll blog code
  if not Dir.exists?("./_site")
    sh "stack exec site build"
  else
    sh "stack exec site rebuild"
  end

  # Make sure every directory without index.html has one
  ensure_index(File.expand_path('./_site'), File.expand_path('./_site/404.html'))

  # Update smt.github.io submodule
  sh "rm -rf smt.github.io/*"
  sh "cp -r _site/* smt.github.io"
  sh "cd smt.github.io && git checkout CNAME && git checkout .nojekyll"
end

task :monitor do
  sh "stack exec site watch"
end

task :serve do
  sh "stack exec site server"
end

task :clean do
  sh "stack exec site clean"
end

task :deploy do
  sh "cd smt.github.io && git add -A && git commit -m 'Update site content' && git push origin hakyll"
end
