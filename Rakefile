require 'rubygems/package_task'

task :default => [:package]

def parse_version
    version = nil
    File.open('wp-discourse.php', 'r') do |file|
        while (!version and line = file.gets)
            /^Version:\s+([0-9\.]+)/ =~ line
            version = $1
        end
    end
    version
end

Rake::PackageTask.new('wp-discourse', parse_version) do |p|
    p.need_zip = true
    p.package_files.include('LICENSE')
    p.package_files.include('comments.php')
    p.package_files.include('wp-discourse.php')
end