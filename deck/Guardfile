require 'find'
require 'erb'
require 'asciidoctor'
require 'asciidoctor/cli/options'
require 'asciidoctor/cli/invoker'

notification :off

#asciidoc -T asciidoctor-backends/slim -a data-uri -a linkcss!
group :development do
  guard :shell do
    watch (/^.+\.adoc$/) { |m| Asciidoctor::Cli::Invoker.new(%W(-b dzslides -T asciidoctor-backends/slim/dzslides #{m[0]})).invoke! }
  end


  ## Look for specified files in the current and child directories.
  ## `find` requires Ruby 1.9 or greater.
  if Find.find(Dir.pwd).detect{|dir|dir=~/.+\.(css|js|html?|php|inc|theme)$/}
    guard :livereload do
      watch(%r{.+\.(css|js|html?|php|inc|theme)$})
    end
  end
end