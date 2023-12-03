desc "Setup the server for letsencrypt"
task :setup do
  puts "create /letsencrypt/acme.json on the server"
  system "ssh root@195.201.135.250 -- \"mkdir -p /letsencrypt && touch /letsencrypt/acme.json && chmod 600 /letsencrypt/acme.json\""
end