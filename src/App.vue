<template>
  <div class="container">
    <SearchBar @termchange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo" />
      <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
    </div>

  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
import VideoDetail from './components/VideoDetail.vue';
import axios from 'axios';
const API_KEY='AIzaSyDbPIcQXXBcHkirmI3f2sVyvDNyfG6y3MU';

export default {
  components : {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data () {
    return {
      videos: [],
      selectedVideo: null
    }
  },
  methods : {
    onTermChange(searchItem) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchItem
        }
      })
      .then(response => {
        this.videos = response.data.items;
      })
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
}
</script>
