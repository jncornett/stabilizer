directory 'build/test/www'
directory 'build/test/www/lib'

file 'build/test/www/index.html' => ['build/test/www'] do |t|
  cp 'test/index.html', t.name
end

file 'build/test/www/lib/stabilizer.js' => ['build/test/www/lib'] do |t|
  cp 'lib/stabilizer.js', t.name
end

task build: [
  'build/test/www/index.html',
  'build/test/www/lib/stabilizer.js'
]

task serve: :build do
  Dir.chdir 'build/test/www'  do
    sh 'python -m http.server'
  end
end

task :clean do
  rm_rf 'build'
end
