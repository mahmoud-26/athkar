<template>
  <div class="container">
    <Card id="1" info="أفضل الذكر بعد القرآن الكريم">
      لا إله إلا الله
    </Card>
    <Card id="2" info="قال الله تبارك وتعالى يا ابن آدم إنك ما دعوتني ورجوتني غفرت لك على ما كان فيك ولا أبالي يا ابن آدم لو بلغت ذنوبك عنان السماء ثم استغفرتني غفرت لك ولا أبالي يا ابن آدم إنك لو أتيتني بقراب الأرض خطايا ثم لقيتني لا تشرك بي شيئا لأتيتك بقرابها مغفرة">
      أستغفر الله
    </Card>
    <Card id="3" info="من قال سبحان الله وبحمده في يوم مائة مرة حطت خطاياه وإن كانت مثل زبد البحر">
      سبحان الله وبحمده
    </Card>
    <Card id="4" info="تملأ الميزان">
      الحمد لله
    </Card>
    <Card id="5" info="كتبت له عشرون حسنة وحطت عنه عشرون سيئة">
      الله أكبر
    </Card>
    <Card id="6" info="من صلى علي صلاة واحدة صلى الله عليه عشر صلوات وحطت عنه عشر خطيئات ورفعت له عشر درجات">
      اللهم صل وسلم وبارك على سيدنا محمد
    </Card>
    <Card id="7" info="تملآن ما بين السماوات والأرض">
      سبحان الله والحمد لله
    </Card>
    <Card id="8" info="كنز من كنوز الجنة">
      لا حول ولا قوة إلا بالله
    </Card>
    <Card id="9" info="كلمتان خفيفتان على اللسان ثقيلتان في الميزان حبيبتان إلى الرحمن">
      سبحان الله وبحمده سبحان الله العظيم
    </Card>
    <Card id="10" info="من قالها في يوم مئة مرة كانت له عدل عشر رقاب و كتبت له مئة حسنة و محيت عنه مئة سيئة و كانت له حرزًا من الشيطان يومه ذلك حتى يمسي و لم يأت أحد بأفضل مما جاء به الا رجل عمل أكثر منه">
      لا إله إلا الله وحده لا شريك له، له الملك و له الحمد وهو على كل شئ قدير
    </Card>
    <Card id="11" info="أحب الكلام إلى الله ومكفرات للذنوب وغرس الجنة وجُنة لقائلهن من النار وأحب إلى النبي ﷺ مما طلعت عليه الشمس والباقيات الصالحات">
      سبحان الله والحمد لله ولا إله إلا الله والله أكبر
    </Card>
    <Card id="12" info="قال النبي ﷺ عجبت لها فُتحت لها أبواب السماء">
      الله أكبر كبيرا والحمد لله كثيرا وسبحان الله بكرة وأصيلا
    </Card>
    <Card id="13" info="قال النبي ﷺ لقد رأيت اثني عشر ملكًا يبتدرونها أيهم يرفعها">
      الحمد لله حمدًا كثيرًا طيبًا مباركًا فيه
    </Card>
    <Total />
    <div class="contact">
      <a href="https://wa.me/+201030740274">
        <i class="fi fi-brands-whatsapp"></i>
      </a>
      <a href="https://github.com/mahmoud-26">
        <i class="fi fi-brands-github"></i>
      </a>
      <a href="mailto:mnaggar2006@gmail.com">
        <i class="fi fi-rr-envelope"></i>
      </a>
    </div>
  </div>
</template>

<script>
  import Card from './components/Card.vue'
  import Total from './components/Total.vue'
  import Swal from 'sweetalert2'

  export default {
    components: { Card, Total },
    data() {
      return {
        done: localStorage.getItem('done')
      }
    },
    mounted() {
      if (this.done === null || this.done === false) {
        Swal.fire({
          title: 'السلام عليكم 👋 مرحبًا بك في موقع أذكار المسلم',
          confirmButtonText: 'التالي'
        }).then(() => {
          Swal.fire({
            title: 'يحتوي الموقع على أذكار إسلامية ثوابها عظيم لقارئها والمواظب عليها',
            confirmButtonText: 'التالي'
          }).then(() => {
            Swal.fire({
              title: 'يمكنك الضغط على الذكر لإظهار بعض الأزرار',
              confirmButtonText: 'التالي'
            }).then(() => {
              Swal.fire({
                title: 'يقوم الزر الأيمن بإظهار معلومات عن الذكر',
                confirmButtonText: 'التالي'
              }).then(() => {
                Swal.fire({
                  title: 'يقوم الزر الأيسر بإعادة العد إلى الصفر',
                  confirmButtonText: 'التالي'
                }).then((result) => {
                  Swal.fire({
                    title: 'لا تنسى المداومة على الذكر حتى يوفقك الله ويرضى عنك 🌹',
                    confirmButtonText: 'إنهاء'
                  })
                  if (result.isConfirmed) {
                    localStorage.setItem('done', true)
                    this.done = localStorage.getItem('done')
                  }
                })
              })
            })
          })
        })
      }
    }
  }
</script>

<style scoped>
  .contact {
    padding-top: 2em;
    display: flex;
    justify-content: space-evenly;
  }
  .contact a {
    font-size: 1.25em;
    color: lightgray;
    text-decoration: none;
  }
  .contact a:active {
    color: black;
  }
</style>