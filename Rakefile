require 'rubygems'
require 'rake'

def jruby?; !!defined?(JRUBY_VERSION); end

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "smartimage"
    gem.summary = %Q{It's like a Swiss Army Knife for images, but one of those tiny ones you can keep on your keychain}
    gem.description = <<-EOD
    SmartImage provides a cross-platform solution for image compositing that works on both MRI and JRuby.
    If using RMagick feels like swatting a fly with a nucler missile, and ImageScience just doesn't get 
    you there, SmartImage is hopefully at that sweet spot in the middle
    EOD
    
    gem.email = "tony@medioh.com"
    gem.homepage = "http://github.com/tarcieri/smartimage"
    gem.authors = ["Tony Arcieri"]
    gem.add_dependency "imagesize", ">= 0.1.1"
    gem.add_dependency "rmagick",   ">= 2.12.2" unless jruby?
    gem.add_development_dependency "rspec", ">= 1.2.9"
    gem.platform = "java" if jruby?
    
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

require 'spec/rake/spectask'
Spec::Rake::SpecTask.new(:spec) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.spec_files = FileList['spec/**/*_spec.rb']
end

Spec::Rake::SpecTask.new(:rcov) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.pattern = 'spec/**/*_spec.rb'
  spec.rcov = true
end

task :spec => :check_dependencies

task :default => :spec

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "smartimage #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
