# Get latest version of alpine distribution
FROM alpine

# Update apk index then install vim
RUN apk update && apk add vim

# Open vim, the ["cmd"] form is prefered
ENTRYPOINT ["vim"]

# docker build -t alpine-vim path/to/Dockerfile/directory
# docker run -it alpine-vim
# https://github.com/JAremko/alpine-vim/blob/master/alpine-vim-base/Dockerfile
