require 'yaml'

file = File.open('./services.yaml')
services = YAML.load(file)

task :clone do
  services.each do |id, service|
    sh "rm -rf ./repo_tmp/#{id} 2>&1"
    sh "git clone #{service['repo']} ./tmp/#{id} -b #{service['branch'] || 'master'} --single-branch --depth=1 2>&1"
  end
end

task :create_redoc_html do
  services.each do |id, service|
    sh "rm -rf ./redoc_tmp/#{id} 2>&1"
  end
end

task :update_postman_collection do
  services.each do |id, service|
  end
end

task :create_api_content do
  services.each do |id, service|
  end
end