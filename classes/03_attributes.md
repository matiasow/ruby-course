!SLIDE
# Attributes


!SLIDE
# Attributes

    @@@ Ruby
    class Article
      @@year = 2011
      def initialize(title)
        @title = title
      end
    end
    
    a = Article.new("I'm a Rubyist")
    
    # How to get the @title or the @@year?


!SLIDE
# Attributes 

    @@@ Ruby
    class Article
      def initialize(title)
        @title = title
      end
      
      def title           # <- Getter
        @title
      end
      def title=(value)   # <- Setter
        @title = value
      end
    end
    
    a = Article.new("I'm a Rubyist")
    a.title
    # => "I'm a Rubyist"

    a.title = "I'm a programmer"
    a.title
    # => "I'm a programmer"


!SLIDE
# Attributes

    @@@ Ruby
    class Article
      attr_accessor :title  # <- Setter + Getter
      
      def initialize(title)
        @title = title
      end
    end
    
    a = Article.new("I'm a Rubyist")
    a.title
    # => "I'm a Rubyist"

    a.title = "I'm a programmer"
    a.title
    # => "I'm a programmer"


!SLIDE
# Attributes

    @@@ Ruby
    class Article
      attr_accessor :title  # <- Setter + Getter
      attr_writer :title    # <- Setter
      attr_reader :title    # <- Getter
    end


!SLIDE
# Attributes

    @@@ Ruby
    class Article
      attr_accessor :title

      def initialize(title)
        # @title = title
        self.title = title  # <- use self.attribute
      end
    end


!SLIDE
# Attributes

    @@@ Ruby
    class Article
      attr_accessor :title

      def initialize(title)
        # @title = title
        self.title = title
      end
      
      def title=(value)
        @title = value.nil? ? value : value.to_s.strip
      end
    end
    
    Article.new("I'm a Rubyist").title
    # => "I'm a Rubyist"
    
    Article.new("  I'm a Rubyist   ").title
    # => "I'm a Rubyist"


!SLIDE
# Class Attributes

    @@@ Ruby
    class Article
      @@year = 2011

      def self.year           # <- Getter
        @@year
      end
      def self.year=(value)   # <- Setter
        @@year = value
      end
    end
    
    Article.year
    # => 2011
    
    Article.year = 2020
    Article.year
    # => 2020

