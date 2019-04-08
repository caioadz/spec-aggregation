require 'yaml'

file = File.open('./services.yaml')
services = YAML.load(file)

task :clone do
  services.each do |id, service|
    tmp_dir = "./tmp/git/#{id}"

    sh "rm -rf #{tmp_dir} 2>&1"
    sh "git clone #{service['repo']} #{tmp_dir} -b #{service['branch'] || 'master'} --single-branch --depth=1 2>&1"
  end
end

task :create_redoc_html do
  services.each do |id, service|
    tmp_dir = "./tmp/redoc/#{id}"
    spec_path = "#{service['spec_dir']}/#{service['spec_file']}"

    sh "rm -rf #{tmp_dir} 2>&1"
    sh "mkdir -p #{tmp_dir}"
    sh "mv ./tmp/git/#{id}/#{spec_path} #{tmp_dir}"

    redoc_file = File.new("#{tmp_dir}/redoc.html", 'w')

    redoc_file.puts('<html>')
    redoc_file.puts('<body>')
    redoc_file.puts("<redoc spec-url=\'#{service['spec_file']}\'></redoc>")
    redoc_file.puts('<script src="https://cdn.jsdelivr.net/npm/redoc@next/bundles/redoc.standalone.js"> </script>')
    redoc_file.puts('</body>')
    redoc_file.puts('</html>')

    redoc_file.close
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