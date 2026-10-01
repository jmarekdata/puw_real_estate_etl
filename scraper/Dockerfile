version: '3.8'

services:
  postgres_db:
    image: postgres:15
    container_name: real_estate_db
    restart: always
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: supertajnehaslo123
      POSTGRES_DB: real_estate_data
    ports:
      - "5432:5432"
    volumes:
      - ./database/data:/var/lib/postgresql/data
      - ./database/init.sql:/docker-entrypoint-initdb.d/init.sql

  scraper:
    build: ./scraper
    container_name: real_estate_scraper
    depends_on:
      - postgres_db
    volumes:
      - ./scraper:/app
    environment:
      DB_HOST: postgres_db
      DB_NAME: real_estate_data
      DB_USER: admin
      DB_PASSWORD: supertajnehaslo123