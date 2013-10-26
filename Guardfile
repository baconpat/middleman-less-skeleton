require 'guard/guard'

module ::Guard
  class LessWatcher < ::Guard::Guard

    def start
      run_on_changes([])
    end

    def reload
      start
      stop
    end

    # Default behaviour on file(s) changes that the Guard plugin watches.
    # @param [Array<String>] paths the changes files or paths
    # @raise [:task_has_failed] when run_on_change has failed
    # @return [Object] the task result
    #
    def run_on_changes(paths)
      dest_path = "source/stylesheets/application.css.less"
      return if paths == [dest_path]

      new_number = if File.exists?(dest_path)
                     contents = File.read(dest_path)
                     if contents =~ %r{// (\d+)}
                       $1.to_i + 1
                     end
                   end

      new_number = new_number.to_i

      template = File.read("source/stylesheets/application-template.css.less")

      File.open(dest_path, 'w') do |file|
        file.write(template.gsub(%r{// (\d+)}) { "// #{new_number}"})
      end
    end
  end
end

guard :less_watcher do
  watch(%r{^source/stylesheets/(.+)\.less$})
end

