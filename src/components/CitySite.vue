<template>
  <router-link
    class="card"
    :to="{
      name: 'description',
      params: {
        id: citySite.ID,
        cityLink: cityLink,
        name: citySite.Name,
      },
    }"
  >
    <div class="citySite_card">
      <div class="citySite_card_thumbnail">
        <img
          v-if="citySite.Picture.PictureUrl1"
          :src="citySite.Picture.PictureUrl1"
          :alt="citySite.Picture.PictureUrl1PictureDescription1"
        />
        <img v-else src="@/assets/replacedImg.png" alt="暫時圖片" />
      </div>
      <div class="citySite_card_body">
        <h4>{{ citySite.Name }}</h4>
        <div class="address">
          <img src="@/assets/location.svg" alt="" />
          <span v-if="citySite.Address">{{ citySite.Address }}</span>
          <span v-else>待更新</span>
        </div>
        <div class="openTime">
          <img src="@/assets/time.svg" alt="" />
          <span v-if="citySite.OpenTime">{{ citySite.OpenTime }}</span>
          <span v-else>全日開放</span>
        </div>
        <div class="ticketInfo">
          <img src="@/assets/money.svg" alt="" />
          <span v-if="citySite.TicketInfo">{{ citySite.TicketInfo }}</span>
          <span v-else>不收費</span>
        </div>
      </div>
    </div>
  </router-link>
</template>

<script>
export default {
  name: 'citySite',
  props: ['citySite', 'cityLink'],
  data() {},
}
</script>

<style lang="scss" scoped>
.card {
  // outline: 1px solid green;  //delete
  &:hover {
    // border: 1px solid grey; //delete
    // border-radius: 20px; //delete
  }
}
.citySite_card {
  display: flex;
  min-width: 200px;
  min-height: fit-content;
  height: 100%;
  padding-bottom: 20px;
  margin-bottom: 20px;
  border-bottom: 1px solid #aeaeae;
  color: black;

  &_thumbnail {
    width: 150px;
    height: 150px;
    flex: 0 0 auto;
    margin-right: 20px;
    overflow: hidden;
    border-radius: 20px; //delete

    img {
      width: 100%;
      height: 100%;
      vertical-align: bottom;
      border-radius: 8px;
      object-fit: cover;
      object-position: center center;

      &:hover {
        transform: scale(1.2);
      }
    }
  }
  &_body {
    // outline: 1px solid red; //delete
    text-align: start;
    overflow: hidden;
    h4 {
      font-size: 20px;
      margin-bottom: 10px;
    }
    div {
      display: flex;
      margin-bottom: 5px;
      // outline: 1px solid green; //delete
      img {
        margin-right: 5%;
      }
      img + span {
        display: -webkit-box;
        -webkit-box-orient: vertical;
        -webkit-line-clamp: 2;
        overflow: hidden;
      }
    }
  }
}
</style>
