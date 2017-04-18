TEST_ROOT = 'build/test/www'
directory TEST_ROOT

TEST_LIB_ROOT = File.join(TEST_ROOT, 'lib')
directory TEST_LIB_ROOT

TEST_FILES = FileList.new('test/*')

BUILT_TEST_FILES = []
TEST_FILES.each do |f|
  btf = File.join(TEST_ROOT, File.basename(f))
  BUILT_TEST_FILES << btf
  file btf => TEST_ROOT do
    cp f, btf
  end
end

task :test_files => BUILT_TEST_FILES

LIB_FILES = FileList.new('lib/*')
BUILT_LIB_FILES = []
LIB_FILES.each do |f|
  blb = File.join(TEST_LIB_ROOT, File.basename(f))
  BUILT_LIB_FILES << blb
  file blb => TEST_LIB_ROOT do
    cp f, blb
  end
end

task :lib_files => BUILT_LIB_FILES

task :build => [:test_files, :lib_files]

task :clean do
  rm_rf TEST_ROOT
end

task :serve => [:build] do
  Dir.chdir(TEST_ROOT) do
    sh 'python -m http.server'
  end
end

