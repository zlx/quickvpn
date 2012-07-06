task :default => [:test]

task :test do
  `rm ~/google_appengine -rf`

  puts "unzip appengine"
  `unzip google_appengine_1.7.0.zip -d ~`
  puts "unzip goagent"
  `unzip goagent-1.0.zip -d ~/google_appengine/`

  puts 'input your google engine appid:'
  appid = gets
  system "sed", "-i", "s*your_appid*#{appid}*", "~/google_appengine/goagent/server/python/app.yaml"

  puts "connect to google server to start server"
  #upload to server
  `sudo python ~/google_appengine/appcfg.py update ~/google_appengine/goagent/server/python`

  system "sed", "-i", "s*your_appid*#{appid}*", "~/google_appengine/goagent/local/proxy.ini"
  puts "start proxy"
  `sudo python ~/google_appengine/goagent/local/proxy.py`

end
