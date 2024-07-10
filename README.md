# FastAPI pet project - Goodreads website simulation   
## How to start the app?
1) Start a virtual environment
virtualenv venv
/venv/scripts/activate
2) Install required packages
pip install -r requirements.txt
3) Start the database
docker run --name postgres -e POSTGRES_PASSWORD=postgres -p 5432:5432 postgres
alembic revision -m 'initial_migration' --autogenerate
alembic upgrade head
4) Start redis
docker run -d --name redis -p 6379:6379 redis/redis-stack-server:latest
## Here is how your docker should look like if everything works
![docker](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/b89365dd-ee98-4492-9620-2110782918cd)
5) Start the main app
(venv) PS C:\Users\Админ\Desktop\adv backend\fast> uvicorn main:app --reload
5) Start in a separate terminal
PS C:\Users\Админ\Desktop\adv backend\fast\dramatiq_job> dramatiq main
6) Start the test server on a separate port
(venv) PS C:\Users\Админ\Desktop\adv backend\fast\test_server> uvicorn main:app --reload --port 9000  
## Here is how your swagger should look like if everything works:

![swagger1](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/b02242bb-ba71-488c-9195-0a0c52f39708)   

![swagger2](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/606be07a-e01d-47f5-acd7-a8a8e2d879c5)   

![swagger3](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/601396fe-6350-4938-9194-8ef907ec6d54)   

