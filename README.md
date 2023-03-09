<div id="header" align="center">
  <img src="https://res.cloudinary.com/teepublic/image/private/s--RX5XjNhT--/t_Preview/b_rgb:191919,c_lpad,f_jpg,h_630,q_90,w_1200/v1540487366/production/designs/1185320_3.jpg" width="100"/>
</div>

name: Latest blog post workflow
on:
  schedule: # Run workflow automatically
    - cron: '0 * * * *' # Runs every hour, on the hour
  workflow_dispatch: # Run workflow manually (without waiting for the cron to be called), through the Github Actions Workflow page directly

jobs:
  update-readme-with-blog:
    name: Update this repo's README with latest blog posts
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Pull in dev.to posts
        uses: gautamkrishnar/blog-post-workflow@master
        with:
          feed_list: "https://habr.com/ru/rss/users/daniilshat/posts/?fl=ru"
