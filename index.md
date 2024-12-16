---
layout: single
author_profile: true
classes: wide
---

I am passionate about using technology to change the world! And about technology as a whole. My goal is to create robust, safe, and beneficial Artificial Intelligence and my interests span the power set of research, machine learning, quantitative technologies, and anything futuristic (ex: AR/VR, automation, robotics).

I have been very fortunate to work at [Two Sigma](https://www.twosigma.com/) and [Cognex](https://www.cognex.com/) focusing on research, development, and productization of machine learning across industries such as quantitative finance and factory automation.

I completed my Master's and Bachelor's in Computer Science at Brown University where I had the opportunity to research machine learning/robotics as well as intern at [NVIDIA](https://www.nvidia.com/) and [Cognex](https://www.cognex.com/).

In my free time, I do things like teaching [Taekwondo at Columbia](https://www.instagram.com/cutaekwondo/), [photography](https://www.instagram.com/thosehippos/), rock climbing, and music.

For my musings across topics, see my [blog](https://medium.com/@thosehippos). For a full list of publications, talks, awards, and academic activities, please see my [bio](/bio). 


## Recent Blog Posts

<div id="medium-posts">
    <!-- Posts will be inserted here -->
</div>

<style>
.medium-post {
    margin-bottom: 2.5rem;
    padding-bottom: 2rem;
    border-bottom: 1px solid #e0e0e0;
}

.medium-post:last-child {
    border-bottom: none;
}

.medium-post h2 {
    margin-top: 0;
    margin-bottom: 0.5rem;
    font-size: 1.2rem;  /* Reduced from 1.5rem */
    line-height: 1.4;
    font-weight: normal;  /* Making it less prominent */
}

.medium-post h2 a {
    text-decoration: none;
    color: #2c5282;
    transition: color 0.2s ease;
}

.medium-post h2 a:hover {
    text-decoration: underline;
    color: #1a365d;
}

.post-meta {
    font-size: 0.9rem;
    color: #666;
    margin-bottom: 1rem;
}

.post-excerpt {
    position: relative;
    background-color: #f8f9fa;
    padding: 1.25rem;
    border-left: 3px solid #e2e8f0;
    margin-top: 0.75rem;
    line-height: 1.6;
    color: #2d3748;
}

.error-message {
    padding: 1rem;
    background-color: #fff5f5;
    border-left: 3px solid #fc8181;
    color: #c53030;
}
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const mediumFeed = 'https://api.rss2json.com/v1/api.json?rss_url=https://medium.com/@thosehippos/feed';
    const postsContainer = document.getElementById('medium-posts');
    
    // Add loading state
    postsContainer.innerHTML = '<div class="post-excerpt">Loading recent blog posts...</div>';
    
    fetch(mediumFeed)
        .then(response => response.json())
        .then(data => {
            if (!data.items || data.items.length === 0) {
                throw new Error('No posts found');
            }
            
            // Clear loading state
            postsContainer.innerHTML = '';
            
            data.items.forEach(post => {
                // Clean up the excerpt text
                let excerpt = post.description
                    .replace(/<[^>]*>/g, '') // Remove HTML tags
                    .replace(/&nbsp;/g, ' ') // Replace HTML spaces
                    .substring(0, 200) // Get first 200 characters
                    .trim(); // Remove extra whitespace
                
                // Add ellipsis only if we actually truncated
                if (post.description.length > 200) {
                    excerpt += '...';
                }
                
                const postDate = new Date(post.pubDate).toLocaleDateString('en-US', {
                    year: 'numeric',
                    month: 'numeric',
                    day: 'numeric'
                });
                
                const postHtml = `
                    <article class="medium-post">
                        <h2>
                            <a href="${post.link}" target="_blank" rel="noopener noreferrer">
                                ${post.title}
                            </a>
                        </h2>
                        <time class="post-meta" datetime="${new Date(post.pubDate).toISOString()}">
                            ${postDate}
                        </time>
                        <div class="post-excerpt">
                            ${excerpt}
                        </div>
                    </article>
                `;
                
                postsContainer.insertAdjacentHTML('beforeend', postHtml);
            });
        })
        .catch(error => {
            console.error('Error fetching Medium posts:', error);
            postsContainer.innerHTML = `
                <div class="error-message">
                    Unable to load blog posts at this time. Please try again later.
                </div>
            `;
        });
});
</script>