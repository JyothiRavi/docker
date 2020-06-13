FROM mongo:3.6.18-xenial

# Add mongo key
ADD $PWD/mongo_key /mongo_key
RUN chmod 400 /mongo_key
RUN chown mongodb:mongodb /mongo_key

