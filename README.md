1)Clone repo, move to required directory
git clone https://github.com/dockersamples/example-voting-app.git
cd example-voting-app
2)Cut docker-compose file to 5 for each service
nano docker-compose-db.yaml
nano docker-compose-redis.yaml
nano docker-compose-worker.yaml
nano docker-compose-vote.yaml
nano docker-compose-result.yaml
3)Install docker-compose and run all preapared files
sudo su
curl -L "https://github.com/docker/compose/releases/download/1.28.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
docker-compose -f docker-compose-db.yaml -f docker-compose-redis.yaml -f docker-compose-worker.yaml -f docker-compose-vote.yaml -f docker-compose-result.yaml up -d
4)Results in console:
Creating example-voting-app_redis_1 ... done
Creating example-voting-app_db_1    ... done
Creating example-voting-app_vote_1  ... done
Creating example-voting-app_result_1 ... done
Creating example-voting-app_worker_1 ... done
6)Apps can be reached here:
http://35.192.122.213:5000/
http://35.192.122.213:5001/
5)Push files to github
exit
git add *
git commit -m "new docker-compose files"
git remote set-url origin git@github.com:elenarazguliaeva/docker.git
git push
