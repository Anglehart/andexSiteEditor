<template>
  <div id="app">
    <h1>Редактор магазина AndexGeo</h1>
    <el-row>
      <p>Скрытие изображений реализовано через Socket.io</p>
      <el-switch
          @change="toggleImages"
          :value="getImagesStatus"
          active-text="Показать фото"
          inactive-text="Скрыть фото">
      </el-switch>
    </el-row>
    <el-row type="flex" justify="center">
      <el-col :span="10">
        <el-input type="textarea" v-model="urls" rows="10"></el-input>
      </el-col>
    </el-row>
     <el-row type="flex" justify="center">
      <el-col>
        <el-button type="primary" rows="10" @click="handleGetParser">
          Парсинг
        </el-button>
      </el-col>
    </el-row>
    <el-row>
      <ul v-for="(item, idx) in parserResult" :key="idx">
        <li>{{item}}</li>
      </ul>
    </el-row>
    <el-table
        :data="productsList"
        style="width: 100%"
        empty-text='Нажмите кнопку "Показать"'
    >
      <el-table-column
          v-if="getImagesStatus"
          label="Фото"
          width="90">
        <template slot-scope="scope">
          <img v-if="getImagesStatus" :src="'https://andexgeo.ru/components/com_jshopping/files/img_products/'+scope.row.image" width="90">
        </template>
      </el-table-column>
      <el-table-column
          prop="id"
          label="ID"
          width="100">
      </el-table-column>
      <el-table-column
          prop="name"
          label="Имя">
      </el-table-column>
      <el-table-column
          prop="price"
          label="Цена">
      </el-table-column>
    </el-table>
    <el-row style="padding-top: 15px">
      <el-button @click="onShowMore" type="primary">Показать еще 10</el-button>
    </el-row>
  </div>
</template>

<script src="./mainpage.js"></script>
<style lang="css" src="./mainpage.css"></style>
