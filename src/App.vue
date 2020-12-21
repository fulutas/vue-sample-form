<template>
  <div class="container">
    <h3>Form Verileri</h3>
    <hr>
    <div class="row">
      <div class="col-md-6">
        <div class="panel panel-warning">
          <div class="panel-heading">
            <h4>Başvuru Formu</h4>
          </div>
          <div class="panel-body">
            <form>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="email">Kullanıcı Adı</label>
                    <input type="text" id="username" class="form-control" placeholder="Kullanıcı adı yazınız" v-model.trim="userData.username">
                  </div>
                  <div class="form-group">
                    <label for="password">Şifre</label>
                    <input type="password" id="password" class="form-control" placeholder="Şifre yazınız" v-model.lazy.number.trim="userData.password">
                  </div>
                  <div class="form-group">
                    <label for="age">Yaş</label>
                    <input type="number" id="age" class="form-control" v-model.number.trim="userData.age">
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label for="message">Açıklama</label><br>
                  <textarea id="message" rows="5" cols="45"  class="form-control" placeholder="Açıklama yazınız"  v-model="userData.message"></textarea>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label>
                      <input type="checkbox" value="yazilim" v-model="userData.interest"> Yazılım
                    </label>
                    <label>
                      <input type="checkbox" value="donanim" v-model="userData.interest"> Donanım
                    </label>
                  </div>

                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label>
                    <input name="male" type="radio" value="Erkek" v-model="userData.gender"> Erkek
                  </label>
                  <label>
                    <input name="female" type="radio" value="Kadin" v-model="userData.gender"> Kadın
                  </label>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 from-group">
                  <label>Şehir</label>
                  <select class="form-control" v-model="userData.selectedCity">
                    <option :selected="city == 'İzmir'"  v-for="city in userData.cities">{{ city }}</option>
                  </select>
                </div>
              </div>
               <div class="row">
                <div class="col-md-12 from-group">
                 <app-switch v-model="switched"></app-switch>
                </div>
              </div>
              <hr>
              <div class="row">
                <div class="col-md-12">
                  <button
                    @click.prevent="submit"
                    class="btn btn-primary">Gönder
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-6" v-if="isSubmitted"> <!-- submit yapıldığında form verileri göster. -->
          <div class="panel panel-info">
            <div class="panel-heading">
              <h4>Form Verileri</h4>
            </div>
            <div class="panel-body">
              <p>Kullanıcı Adı: {{ userData.username }}</p>
              <p>Şifre: {{ userData.password }} </p>
              <p>Yaş: {{ userData.age }}</p>
              <p style="white-space : pre;">Açıklama: {{ userData.message }} </p>
              <p><strong>İlgi Alanları</strong></p>
              <ul>
                <li v-for="item in userData.interest"> {{ item }}</li>
              </ul>
              <p>Cinsiyet: {{ userData.gender }} </p>
              <p>Şehir: {{ userData.selectedCity}}</p>
              <p>Toggle: {{ switched }} </p>
            </div>
          </div>
      </div>
    </div>

  </div>
</template>

<script>

  import Switch from './Switch'

  export default {

      data(){
        return {
            userData : {
              username : '',
              password : '',
              age : 20, // Varsayılan değer,
              message : '',
              interest : [], // Checkbox için Array tipinde data
              gender : '',
              cities : ["İstanbul","Ankara","Adana","İzmir","Bursa","Konya","Trabzon","Samsun","Kocaeli"],
              selectedCity : '',
            },
            isSubmitted : false
        }
      },
      methods : {
        submit() {
            this.isSubmitted = true;
        }
      },
      components : {
            appSwitch : Switch,
      }

  }
</script>

<style>

textarea {
resize: vertical;
}

</style>
