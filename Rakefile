require 'rake'
require 'rake/testtask'
require 'rake/rdoctask'
require 'rake/gempackagetask'

desc 'Default: run unit tests.'
task :default => :test

desc 'Test the to_csv plugin.'
Rake::TestTask.new(:test) do |t|
  t.libs << 'lib'
  t.libs << 'test'
  t.pattern = 'test/**/*_test.rb'
  t.verbose = true
end

desc 'Generate documentation for the to_csv plugin.'
Rake::RDocTask.new(:rdoc) do |rdoc|
  rdoc.rdoc_dir = 'rdoc'
  rdoc.title    = 'ToCsv'
  rdoc.options << '--line-numbers' << '--inline-source'
  rdoc.rdoc_files.include('README.rdoc')
  rdoc.rdoc_files.include('lib/**/*.rb')
end


PKG_FILES = FileList[
  '[a-zA-Z]*',
  'generator/**/*',
  'lib/**/*',
  'rails/**/*',
  'tasks/**/*',
  'test/**/*'
]

spec = Gem::Specification.new do |s|
  s.name = 'to_csv'
  s.version = '1.0.0'
  s.author = 'Wenke Liang'
  s.email = 'liangwenke8@gmail.com'
  s.homepage = 'http://github.com/wenke/to_csv'
  s.platform = 'Gem::Platform::RUBY'
  s.summary = 'Transform an Array into a CSV file gem.'
  s.files = PKG_FILES.to_a
  s.require_path = 'lib'
  s.has_rdoc = false
  s.extra_rdoc_files = ["README.rdoc"]
end

desc "Turn this plugin into a gem."
Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end
