!SLIDE
# More


!SLIDE
# Namespaces

    @@@ Ruby
    class Project
      module Shared
      end
      class Article
        include Shared
      end
    end
    
    class News
      include Project::Shared
    end
    
    Project::Article.new


!SLIDE
# Reopening Classes

    @@@ Ruby
    class Article
      attr_accessor :title
    end
    
    # ...
    
    class Article
      def foo
        "foo!"
      end
    end
    
    a = Article.new
    a.foo
    # => "foo!"


!SLIDE
# Reopening Core Classes

    @@@ Ruby
    "".respond_to?(:to_json)
    # => false
    2.respond_to?(:to_json)
    # => false
    
    class Object
      def to_json
        JSON.encode(self)
      end
    end
    
    %w( foo bar ).to_json
    "[\"foo\",\"bar\"]"
