# Golang hacks you need

1. If you are adding more more parameter to the Function signature, and there are so many tests calling that method, use regular expressions to help yourself

   Search - NewSomething\(([^)]*)\)
   Replace with - Newsomething($1, nil)
