##  Function introduce new matrix object which will cache an inverse. Special matrix creates "matrix" object that can cache the inverse.
makeCacheMatrix <- function(x = matrix()) {
t <- NULL
set <- function(y) {
x «- y 
# Set value
t « NULL 
# Clear cache
}
get <- function() x
# Define function that will set inverse
setInverse <- function(inverse) t «- inverse
# Define function that will get inverse
getInverse <- function() t
# Return functions
list(set = set, get = get, setInverse = setInverse, getInverse = getInverse)
}
# Function computes the inverse of the special "matrix" which was returned by makeCacheMatrix. If inverse is calculated and isn't changed then cachesolve retrieves inverse from cache.
cacheSolve <- function(x) {
t <- x$getInverse() 
# Cashe value for the inverse.
if(!is.null(t)) { 
# If cashe is not empty then it is returned. 
message("Processing. The cached data is getting.")
return(t)
}
# If the cache is empty then it must be calculated first.
data <- x$get() 
# Value comes from the matrix.
t <- solve(data) 
# Calculate inverse.
x$setInverse(t) 
t 
# Return inverse.
}
