FROM ruby

RUN apt-get update
RUN apt-get dist-upgrade -y
RUN apt-get install nodejs -y
RUN gem install rails

ONBUILD COPY . /opt/app

ONBUILD WORKDIR /opt/app

ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed

# docker build . -t ft-rails:on-build

# WARNING : THE COMMAND BELOW ONLY WORKS IF YOU'RE IN THE HOME DIRECTORY !
# docker run -it --rm -v "$PWD":/usr/src/app -w /usr/src/app rails rails new --skip-bundle app

# CREATE A NEW DOCKERFILE INSIDE app :
# FROM ft-rails:on-build
# EXPOSE 3000
# CMD ["rails", "s", "-b", "0.0.0.0", "-p" ,"3000"]

# docker build . -t ft-rails
# docker run -d -t 3000:3000 ft-rails
