---
layout: single
author_profile: true
classes: wide
---

I am passionate about using technology to change the world! And about technology as a whole. My goal is to create robust, safe, and beneficial Artificial Intelligence and my interests span the power set of research, machine learning, quantitative technologies, and anything futuristic (ex: AR/VR, automation, robotics).

I have been very fortunate to work at [Two Sigma](https://www.twosigma.com/) and [Cognex](https://www.cognex.com/) focusing on research, development, and productization of machine learning across industries such as quantitative finance and factory automation. Prior to that, I completed my Master's and Bachelor's in Computer Science at Brown University where I had the opportunity to research machine learning/robotics as well as intern at [NVIDIA](https://www.nvidia.com/) and [Cognex](https://www.cognex.com/).

In my free time, I do things like teaching [Taekwondo at Columbia](https://www.instagram.com/cutaekwondo/), [photography](https://www.instagram.com/thosehippos/), rock climbing, and music.

For my musings across topics, see my [blog](https://medium.com/@thosehippos). For a full list of publications, talks, awards, and academic activities, please see my [bio](/bio). 


## Recent Blog Posts

<div id="medium-posts">
    <!-- Posts will be inserted here -->
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    // Medium RSS feed URL with a CORS proxy
    const mediumFeed = 'https://api.rss2json.com/v1/api.json?rss_url=https://medium.com/@thosehippos/feed';
    
    fetch(mediumFeed)
        .then(response => response.json())
        .then(data => {
            const posts = data.items;
            const postsContainer = document.getElementById('medium-posts');
            
            posts.forEach(post => {
                const postDate = new Date(post.pubDate).toLocaleDateString();
                const postHtml = `
                    <article class="medium-post">
                        <h2><a href="${post.link}" target="_blank">${post.title}</a></h2>
                        <div class="post-meta">Published on ${postDate}</div>
                        <div class="post-excerpt">
                            ${post.description.substring(0, 200)}...
                        </div>
                    </article>
                `;
                postsContainer.innerHTML += postHtml;
            });
        })
        .catch(error => {
            console.error('Error fetching Medium posts:', error);
        });
});
</script>