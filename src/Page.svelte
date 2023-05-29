<script>
    let videoId = 'dQw4w9WgXcQ';
    let videoTitle = 'Rick Astley - Never Gonna Give You Up (Official Music Video)';
    let videoDescription = 'The official video for “Never Gonna Give You Up” by Rick Astley';
    let videoUploader = 'Rick Astley'
    let videoSubscribers = '3.5M'
    let videoUploadTimes = 'Oct 24, 2009'

    let suggestedVideos = [
        {
        id: 'AI4ynXzkSQo',
        title: 'The Ultimate V60 Technique',
        description: 'This is my recommended technique for making coffee with the Hario V60, and any other cone-shaped brewer with a large open area.',
        uploader: "James Hoffman",
        subscribers: '1.77M',
        uploadTime: 'Aug 5, 2019'
        },
        {
        id: '32GZ3suxRn4',
        title: 'Slow Dancing In A Burning Room (Live in L.A.)',
        description: 'From Where The Light Is',
        uploader: "codyates2181",
        subscribers: '50.6k',
        uploadTime: 'Jul 26, 2008'
        },
        {
        id: 'e-hMKIN2n3g',  
        title: 'UC Berkeley: Just Getting Started',
        description: 'On March 23, 1868, the University of California was born — and Berkeley, its first campus, is one of the greatest sources of research and knowledge the world has ever known. Produced by UC Berkeley, this video marks Berkeley 150, the year-long sesquicentennial celebration, as both the culmination of 150 years of light and an inspiring call to action to sustain our brilliance for another 150 years. Featuring excerpts from Chancellor Carol T. Christ’s keynote address on Charter Day, March 23, 2018.',
        uploader: "UC Berkeley: Light the Way",
        subscribers: '41.2k',
        uploadTime: 'Apr 24, 2019'
    },
    ];

    function selectVideo(id) {

        // let toReplace = suggestedVideos.findIndex(x => x.id === id);
        // let currentVideo = {
        //     id: videoId,
        //     title: videoTitle,
        //     description: videoDescription,
        // }

        videoId = id;
        let nextVideo = suggestedVideos.find(video => video.id === id)
        videoTitle = nextVideo.title
        videoDescription = nextVideo.description
        videoUploader = nextVideo.uploader
        videoSubscribers = nextVideo.subscribers
        videoUploadTimes = nextVideo.uploadTime
        
        // suggestedVideos.splice(toReplace, 1, currentVideo)
    }
</script>


<!-- navigation bar -->
<div id="navbar">
  <div id="title">MyTube</div>
  <div id="search-container">
    <input id="search" type="search" placeholder="I want to watch..." />
  </div>
</div>

<!-- main video player -->
<div id="video-player">
    <iframe width="560" height="315" title='video' src="https://www.youtube.com/embed/{videoId}" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<!-- video info -->
<div id="video-info">
    <h1 id="video-title">{videoTitle}</h1>

      <div id="uploader-info">
        <h3>Uploaded by {videoUploader}</h3>
        <h4>{videoSubscribers} subscribers</h4>
        <button id="subscribe-button">Subscribe</button>
      </div>

      <div id="video-details">
        <h4>Posted on {videoUploadTimes}</h4>
        <button id="like-button">👍 Like</button>
      </div>

    <p id="video-description">{videoDescription}</p>
</div>

<!-- suggested videos list -->
<div id="suggested-videos">
    <h2>Suggested Videos</h2>
    <ul>
        {#each suggestedVideos as video}
        <li>
            <h3>{video.title}</h3>
            <p>{video.uploader}</p>
            <button on:click={() => selectVideo(video.id)}>Watch</button>
        </li>
        {/each}
    </ul>
</div>


<style>
    /* Navigation Bar Style */
    #navbar {
        display: flex;
        justify-content: space-between;
        padding: 1em;
        background-color: #f00;
    }
    #title {
        color: #fff;
        font-size: 1.5em;
    }
    #search-container {
        position: relative;
        width: 200px;
    }
    #search {
        width: 100%;
        padding: 0.5em;
    }
    #search-container::before {
        content: '🔍';
        position: absolute;
        right: 5px;
        top: 50%;
        transform: translateY(-50%);
        font-size: 1em;
        pointer-events: none;
    }

    /* Video Player Style */
    #video-player {
        width: 60%;
        height: 0;
        padding-bottom: 33.75%;
        position: relative;
        margin: 1em auto;
    }
    #video-player iframe {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }

    /* Video Info Style */
    #video-info {
        color: #333;
        width: 60%;
        margin: 1em auto;
    }

    #video-title {
        font-size: 1.5em;
        font-weight: bold;
    }

    /* Suggested Videos List */
    #suggested-videos {
        width: 30%;
        margin: 1em;
        float: right;
    }
    #suggested-videos h2 {
        font-size: 1.2em;
        margin-bottom: 0.5em;
    }
    #suggested-videos ul {
        list-style-type: none;
        padding: 0;
    }
    #suggested-videos li {
        margin-bottom: 1em;
        padding: 1em;
        background-color: #fff;
        border: 1px solid #ddd;
        border-radius: 4px;
    }
    #suggested-videos li h3 {
        font-size: 1em;
        margin-bottom: 1em;
    }
    #suggested-videos button {
        background-color: #f00;
        color: #fff;
        border: none;
        padding: 0.5em 1em;
        border-radius: 2px;
        cursor: pointer;
    }
    #suggested-videos button:hover {
        background-color: #c00;
    }
</style>