# FastAPI pet project - Goodreads website simulation   
## What can this app do?
1) You can sign up as a user
2) Log in as a user and use the 'log in' response body as a token to get authorized.
As an authorized user you can create authors, books, genres, quotes and book reviews. Without logging in you can only read the lists of authors, books, genres, quotes and book reviews that other people left.

![signup](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/f45c5f8e-eced-46a3-91b7-173ffbf9848f)

![signupresponse](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/9447fcc4-b74b-41c3-9a76-6fecfcce6727)    

![jwtbearer](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/c6ebdc53-63e5-441c-81be-04b3dd7819ab)    
3) After registering on our website you get a welcoming email with the pdf file of book recommendations for this month.
Book recommendations are being scraped from the New York Times Bestsellers of this month. Here is the link:
https://www.nytimes.com/books/best-sellers/combined-print-and-e-book-fiction/
This pdf list contains: book name, author name, book description and book cover.    
Dramatiq is used here to support the background task.
Scraping is used here to automate the task, reportlab library is used for pdf generation and email.mime  with smtplib libraries are used to send the email to the user.
![email](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/ffb7543a-425a-4ce2-8330-978cbdf6c82c)   

4) You can also join our telegram channel. After first talking to the channel it tells you your chatID, after giving us your chatID through '/send_pdf_to_tg' endpoint, it will send you that recommendations pdf in telegram channel also.   
Dramatiq is used here to support the background task.

![telegram](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/9607fb2a-7d05-4b75-a2a4-43f92366999d)   


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
5) Start the main app
(venv) PS C:\Users\Админ\Desktop\adv backend\fast> uvicorn main:app --reload
5) Start in a separate terminal
PS C:\Users\Админ\Desktop\adv backend\fast\dramatiq_job> dramatiq main
6) Start the test server on a separate port
(venv) PS C:\Users\Админ\Desktop\adv backend\fast\test_server> uvicorn main:app --reload --port 9000

## Here is how your docker should look like if everything works
![docker](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/b89365dd-ee98-4492-9620-2110782918cd)

## Here is how your swagger should look like if everything works:

![swagger1](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/b02242bb-ba71-488c-9195-0a0c52f39708)   

![swagger2](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/606be07a-e01d-47f5-acd7-a8a8e2d879c5)   

![swagger3](https://github.com/orynbay21/Goodreads_FastApi_Pet_Project/assets/98757036/601396fe-6350-4938-9194-8ef907ec6d54)   

