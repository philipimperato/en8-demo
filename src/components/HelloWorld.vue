<template>
  <div class="w-3/4 mx-auto text-left">
    <h1 class="text-4xl text-gray-800 mb-8">Enunc8 score demo</h1>

    <div class="text-lg font-bold">Text to test:</div>
    <div class="text-base text-gray-600">
      your customers are likely already attracting with clients through social media if you aren't speaking to your customers through social platforms like facebook twitter and linkedin you need to rethink your strategy
    </div>
    
    <div class="grid grid-cols-2 gap-8 mb-8">
      <div>
        <div class="text-base mt-8 mb-4">
          <div>
            <h3 class="text-2xl text-gray-900">
              <span class="font-bold">Before</span> Enunc8 - Overall score
              <audio controls>
                <source src="before.wav" type="audio/wav">
                Your browser does not support the audio element.
              </audio>
            </h3>
            <dl class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-4">
              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">
                  AccuracyScore
                </dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">
                  {{ beforeScore.AccuracyScore }}
                </dd>
              </div>
              
              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">
                  CompletenessScore
                </dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">
                  {{ beforeScore.CompletenessScore }}
                </dd>
              </div>

              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">
                  FluencyScore
                </dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">
                  {{ beforeScore.FluencyScore }}
                </dd>
              </div>

              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">
                  PronScore
                </dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">
                  {{ beforeScore.PronScore }}
                </dd>
              </div>
            </dl>
          </div>
        </div>

        <!-- This example requires Tailwind CSS v2.0+ -->
        <div class="bg-white shadow overflow-hidden sm:rounded-md">
          <ul>
            <li class="my-1" v-for="(word, index) in beforeScore.Words" :key="index" 
              :class="{ 
                'border-2 border-red-500 border-solid' : word.AccuracyScore < 80,
                'border-2 border-yellow-300 border-solid' : word.AccuracyScore >= 80 && word.AccuracyScore < 95,
                'border-2 border-green-500 border-solid' : word.AccuracyScore >= 95
              }">
              <a href="#" class="block hover:bg-gray-50">
                <div class="px-2 py-2 flex items-center sm:px-2">
                  <div class="min-w-0 flex-1 sm:flex sm:items-center sm:justify-between">
                    <div class="truncate">
                      <div class="flex text-sm">
                        <p class="font-bold text-lg text-indigo-600 truncate">{{ word.Word }}</p>
                        <p class="flex-shrink-0 font-normal text-gray-500 my-1 mx-2">
                          score of &nbsp;
                        </p>
                        <span class="font-bold text-lg block">{{ word.AccuracyScore }}</span>
                      </div>
                      <div class="mt-1 flex">
                        <div class="flex items-center text-sm text-gray-500">
                          <div>
                            <table>
                              <tr>
                                <td class="border px-4" v-for="(p, index) in word.Phonemes" :key="index">{{ p.Phoneme }} - {{ p.AccuracyScore }}</td>
                              </tr>
                            </table>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </a>
            </li>
          </ul>
        </div>
      </div>

      <div>
        <div class="text-base mt-8 mb-4">
          <div>
            <h3 class="text-2xl text-gray-900">
              <span class="font-bold">After</span> Enunc8 - Overall score
              <audio controls>
                <source src="after.wav" type="audio/wav">
                Your browser does not support the audio element.
              </audio>
            </h3>
            <dl class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-4">
              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">
                  AccuracyScore
                </dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">
                  {{ afterScore.AccuracyScore }}
                </dd>
              </div>
              
              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">
                  CompletenessScore
                </dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">
                  {{ afterScore.CompletenessScore }}
                </dd>
              </div>

              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">
                  FluencyScore
                </dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">
                  {{ afterScore.FluencyScore }}
                </dd>
              </div>

              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">
                  PronScore
                </dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">
                  {{ afterScore.PronScore }}
                </dd>
              </div>
            </dl>
          </div>
        </div>

        <!-- This example requires Tailwind CSS v2.0+ -->
        <div class="bg-white shadow overflow-hidden sm:rounded-md">
          <ul>
            <li class="my-1" v-for="(word, index) in afterScore.Words" :key="index" 
              :class="{ 
                'border-2 border-red-500 border-solid' : word.AccuracyScore < 80,
                'border-2 border-yellow-300 border-solid' : word.AccuracyScore >= 80 && word.AccuracyScore < 95,
                'border-2 border-green-500 border-solid' : word.AccuracyScore >= 95
              }">
              <a href="#" class="block hover:bg-gray-50">
                <div class="px-2 py-2 flex items-center sm:px-2">
                  <div class="min-w-0 flex-1 sm:flex sm:items-center sm:justify-between">
                    <div class="truncate">
                      <div class="flex text-sm">
                        <p class="font-bold text-lg text-indigo-600 truncate">{{ word.Word }}</p>
                        <p class="flex-shrink-0 font-normal text-gray-500 my-1 mx-2">
                          score of &nbsp;
                        </p>
                        <span class="font-bold text-lg block">{{ word.AccuracyScore }}</span>
                      </div>
                      <div class="mt-1 flex">
                        <div class="flex items-center text-sm text-gray-500">
                          <div>
                            <table>
                              <tr>
                                <td class="border px-4" v-for="(p, index) in word.Phonemes" :key="index">{{ p.Phoneme }} - {{ p.AccuracyScore }}</td>
                              </tr>
                            </table>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>

    <div class="text-base mt-16 mb-4">
      <div>
        <h3 class="text-2xl text-gray-900">
          <span class="font-bold">My overall score</span>
        </h3>
        <dl class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-4">
          <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
            <dt class="text-sm font-medium text-gray-500 truncate">
              AccuracyScore
            </dt>
            <dd class="mt-1 text-3xl font-semibold text-gray-900">
              {{ myScore.AccuracyScore }}
            </dd>
          </div>
          
          <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
            <dt class="text-sm font-medium text-gray-500 truncate">
              CompletenessScore
            </dt>
            <dd class="mt-1 text-3xl font-semibold text-gray-900">
              {{ myScore.CompletenessScore }}
            </dd>
          </div>

          <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
            <dt class="text-sm font-medium text-gray-500 truncate">
              FluencyScore
            </dt>
            <dd class="mt-1 text-3xl font-semibold text-gray-900">
              {{ myScore.FluencyScore }}
            </dd>
          </div>

          <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
            <dt class="text-sm font-medium text-gray-500 truncate">
              PronScore
            </dt>
            <dd class="mt-1 text-3xl font-semibold text-gray-900">
              {{ myScore.PronScore }}
            </dd>
          </div>
        </dl>
      </div>
    </div>

    <!-- This example requires Tailwind CSS v2.0+ -->
    <div class="bg-white shadow overflow-hidden sm:rounded-md">
      <ul>
        <li class="my-1" v-for="(word, index) in myScore.Words" :key="index" 
          :class="{ 
            'border-2 border-red-500 border-solid' : word.AccuracyScore < 80,
            'border-2 border-yellow-300 border-solid' : word.AccuracyScore >= 80 && word.AccuracyScore < 95,
            'border-2 border-green-500 border-solid' : word.AccuracyScore >= 95
          }">
          <a href="#" class="block hover:bg-gray-50">
            <div class="px-2 py-2 flex items-center sm:px-2">
              <div class="min-w-0 flex-1 sm:flex sm:items-center sm:justify-between">
                <div class="truncate">
                  <div class="flex text-sm">
                    <p class="font-bold text-lg text-indigo-600 truncate">{{ word.Word }}</p>
                    <p class="flex-shrink-0 font-normal text-gray-500 my-1 mx-2">
                      score of &nbsp;
                    </p>
                    <span class="font-bold text-lg block">{{ word.AccuracyScore }}</span>
                  </div>
                  <div class="mt-1 flex">
                    <div class="flex items-center text-sm text-gray-500">
                      <div>
                        <table>
                          <tr>
                            <td class="border px-4" v-for="(p, index) in word.Phonemes" :key="index">{{ p.Phoneme }} - {{ p.AccuracyScore }}</td>
                          </tr>
                        </table>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      beforeScore: {},
      afterScore: {},
      myScore: {}
    }
  },
  mounted() {
    const bs = 
      {"RecognitionStatus":"Success","Offset":200000,"Duration":124200000,"NBest":[{"Lexical":"your customers are likely already attracting with clients through social media if you aren't speaking to your customers through social platforms like facebook twitter and linkedin you need to rethink your strategy",
      "ITN":"your customers are likely already attracting with clients through social media if you arent speaking to your customers through social platforms like facebook twitter and linkedin you need to rethink your      strategy","MaskedITN":"your customers are likely already attracting with clients through social media if you aren't speaking to your customers through social platforms like facebook twitter and linkedin you need to rethink your strategy",
      "Display":"Your customers are likely already attracting with clients through social media. If you aren't speaking to your customers through social platforms like Facebook, Twitter, and LinkedIn, you need to rethink your strategy.","AccuracyScore":91.0,"FluencyScore":91.0,"CompletenessScore":100.0,
      "PronScore":92.80000000000001,"Words":[{"Word":"your","AccuracyScore":100.0,"ErrorType":"None","Offset":400000,"Duration":2700000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":400000,"Duration":1100000},{"Phoneme":"ao","AccuracyScore":100.0,"Offset":1600000,
      "Duration":700000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":2400000,"Duration":700000}]},{"Word":"customers","AccuracyScore":100.0,"ErrorType":"None","Offset":3200000,"Duration":5100000,"Phonemes":[{"Phoneme":"k","AccuracyScore":100.0,"Offset":3200000,"Duration":500000},
      {"Phoneme":"ah","AccuracyScore":100.0,"Offset":3800000,"Duration":500000},{"Phoneme":"s","AccuracyScore":100.0,"Offset":4400000,"Duration":400000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":4900000,"Duration":400000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":5400000,
      "Duration":300000},{"Phoneme":"m","AccuracyScore":100.0,"Offset":5800000,"Duration":700000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":6600000,"Duration":500000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":7200000,"Duration":300000},{"Phoneme":"z","AccuracyScore":100.0,
      "Offset":7600000,"Duration":700000}]},{"Word":"are","AccuracyScore":96.0,"ErrorType":"None","Offset":8400000,"Duration":800000,"Phonemes":[{"Phoneme":"aa","AccuracyScore":100.0,"Offset":8400000,"Duration":500000},{"Phoneme":"r","AccuracyScore":87.0,"Offset":9000000,
      "Duration":200000}]},{"Word":"likely","AccuracyScore":90.0,"ErrorType":"None","Offset":9300000,"Duration":3800000,"Phonemes":[{"Phoneme":"l","AccuracyScore":63.0,"Offset":9300000,"Duration":400000},{"Phoneme":"ay","AccuracyScore":83.0,"Offset":9800000,"Duration":900000},
      {"Phoneme":"k","AccuracyScore":100.0,"Offset":10800000,"Duration":800000},{"Phoneme":"l","AccuracyScore":95.0,"Offset":11700000,"Duration":400000},{"Phoneme":"iy","AccuracyScore":98.0,"Offset":12200000,"Duration":900000}]},{"Word":"already","AccuracyScore":67.0,"ErrorType":
      "None","Offset":13200000,"Duration":3900000,"Phonemes":[{"Phoneme":"ao","AccuracyScore":75.0,"Offset":13200000,"Duration":1100000},{"Phoneme":"l","AccuracyScore":88.0,"Offset":14400000,"Duration":600000},{"Phoneme":"r","AccuracyScore":62.0,"Offset":15100000,"Duration":300000},
      {"Phoneme":"eh","AccuracyScore":45.0,"Offset":15500000,"Duration":200000},{"Phoneme":"d","AccuracyScore":70.0,"Offset":15800000,"Duration":700000},{"Phoneme":"iy","AccuracyScore":40.0,"Offset":16600000,"Duration":500000}]},{"Word":"attracting","AccuracyScore":80.0,
      "ErrorType":"None","Offset":17200000,"Duration":5700000,"Phonemes":[{"Phoneme":"ax","AccuracyScore":0.0,"Offset":17200000,"Duration":500000},{"Phoneme":"t","AccuracyScore":45.0,"Offset":17800000,"Duration":900000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":18800000,
      "Duration":700000},{"Phoneme":"ae","AccuracyScore":100.0,"Offset":19600000,"Duration":400000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":20100000,"Duration":600000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":20800000,"Duration":500000},{"Phoneme":"ih",
      "AccuracyScore":100.0,"Offset":21400000,"Duration":700000},{"Phoneme":"ng","AccuracyScore":100.0,"Offset":22200000,"Duration":700000}]},{"Word":"with","AccuracyScore":85.0,"ErrorType":"None","Offset":23000000,"Duration":2200000,"Phonemes":[{"Phoneme":"w",
      "AccuracyScore":100.0,"Offset":23000000,"Duration":300000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":23400000,"Duration":400000},{"Phoneme":"th","AccuracyScore":2.0,"Offset":23900000,"Duration":1300000}]},{"Word":"clients","AccuracyScore":51.0,"ErrorType":"None",
      "Offset":25300000,"Duration":4000000,"Phonemes":[{"Phoneme":"k","AccuracyScore":0.0,"Offset":25300000,"Duration":400000},{"Phoneme":"l","AccuracyScore":0.0,"Offset":25800000,"Duration":400000},{"Phoneme":"ay","AccuracyScore":44.0,"Offset":26300000,"Duration":900000},
      {"Phoneme":"ax","AccuracyScore":57.0,"Offset":27300000,"Duration":400000},{"Phoneme":"n","AccuracyScore":36.0,"Offset":27800000,"Duration":200000},{"Phoneme":"t","AccuracyScore":99.0,"Offset":28100000,"Duration":600000},{"Phoneme":"s","AccuracyScore":94.0,"Offset":28800000,
      "Duration":500000}]},{"Word":"through","AccuracyScore":100.0,"ErrorType":"None","Offset":29400000,"Duration":2300000,"Phonemes":[{"Phoneme":"th","AccuracyScore":100.0,"Offset":29400000,"Duration":900000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":30400000,
      "Duration":500000},{"Phoneme":"uw","AccuracyScore":100.0,"Offset":31000000,"Duration":700000}]},{"Word":"social","AccuracyScore":100.0,"ErrorType":"None","Offset":31800000,"Duration":3200000,"Phonemes":[{"Phoneme":"s","AccuracyScore":100.0,"Offset":31800000,
      "Duration":500000},{"Phoneme":"ow","AccuracyScore":100.0,"Offset":32400000,"Duration":700000},{"Phoneme":"sh","AccuracyScore":100.0,"Offset":33200000,"Duration":900000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":34200000,"Duration":300000},
      {"Phoneme":"l","AccuracyScore":100.0,"Offset":34600000,"Duration":400000}]},{"Word":"media","AccuracyScore":97.0,"ErrorType":"None","Offset":35100000,"Duration":5200000,"Phonemes":[{"Phoneme":"m","AccuracyScore":100.0,"Offset":35100000,"Duration":600000},
      {"Phoneme":"iy","AccuracyScore":100.0,"Offset":35800000,"Duration":300000},{"Phoneme":"d","AccuracyScore":100.0,"Offset":36200000,"Duration":500000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":36800000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":94.0,
      "Offset":37400000,"Duration":2900000}]},{"Word":"if","AccuracyScore":100.0,"ErrorType":"None","Offset":43900000,"Duration":2200000,"Phonemes":[{"Phoneme":"ih","AccuracyScore":100.0,"Offset":43900000,"Duration":1600000},{"Phoneme":"f","AccuracyScore":100.0,
      "Offset":45600000,"Duration":500000}]},{"Word":"you","AccuracyScore":100.0,"ErrorType":"None","Offset":46200000,"Duration":1300000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":46200000,"Duration":500000},{"Phoneme":"uw","AccuracyScore":100.0,
      "Offset":46800000,"Duration":700000}]},{"Word":"aren't","AccuracyScore":81.0,"ErrorType":"None","Offset":47600000,"Duration":2500000,"Phonemes":[{"Phoneme":"aa","AccuracyScore":100.0,"Offset":47600000,"Duration":900000},{"Phoneme":"r","AccuracyScore":62.0,
      "Offset":48600000,"Duration":500000},{"Phoneme":"n","AccuracyScore":69.0,"Offset":49200000,"Duration":500000},{"Phoneme":"t","AccuracyScore":82.0,"Offset":49800000,"Duration":300000}]},{"Word":"speaking","AccuracyScore":84.0,"ErrorType":"None","Offset":50200000,
      "Duration":4500000,"Phonemes":[{"Phoneme":"s","AccuracyScore":67.0,"Offset":50200000,"Duration":400000},{"Phoneme":"p","AccuracyScore":100.0,"Offset":50700000,"Duration":1000000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":51800000,"Duration":500000},
      {"Phoneme":"k","AccuracyScore":100.0,"Offset":52400000,"Duration":700000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":53200000,"Duration":700000},{"Phoneme":"ng","AccuracyScore":27.0,"Offset":54000000,"Duration":700000}]},{"Word":"to","AccuracyScore":52.0,
      "ErrorType":"None","Offset":54800000,"Duration":900000,"Phonemes":[{"Phoneme":"t","AccuracyScore":60.0,"Offset":54800000,"Duration":500000},{"Phoneme":"uh","AccuracyScore":1.0,"Offset":55400000,"Duration":300000}]},{"Word":"your","AccuracyScore":66.0,"ErrorType":"None",
      "Offset":55800000,"Duration":3300000,"Phonemes":[{"Phoneme":"y","AccuracyScore":5.0,"Offset":55800000,"Duration":1100000},{"Phoneme":"ao","AccuracyScore":28.0,"Offset":57000000,"Duration":1100000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":58200000,"Duration":900000}]},
      {"Word":"customers","AccuracyScore":100.0,"ErrorType":"None","Offset":59200000,"Duration":5200000,"Phonemes":[{"Phoneme":"k","AccuracyScore":100.0,"Offset":59200000,"Duration":700000},{"Phoneme":"ah","AccuracyScore":100.0,"Offset":60000000,"Duration":500000},
      {"Phoneme":"s","AccuracyScore":100.0,"Offset":60600000,"Duration":300000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":61000000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":61600000,"Duration":500000},{"Phoneme":"m","AccuracyScore":100.0,
      "Offset":62200000,"Duration":400000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":62700000,"Duration":600000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":63400000,"Duration":300000},{"Phoneme":"z","AccuracyScore":100.0,"Offset":63800000,"Duration":600000}]},
      {"Word":"through","AccuracyScore":100.0,"ErrorType":"None","Offset":64500000,"Duration":2400000,"Phonemes":[{"Phoneme":"th","AccuracyScore":100.0,"Offset":64500000,"Duration":1200000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":65800000,"Duration":400000},
      {"Phoneme":"uw","AccuracyScore":100.0,"Offset":66300000,"Duration":600000}]},{"Word":"social","AccuracyScore":100.0,"ErrorType":"None","Offset":67000000,"Duration":3800000,"Phonemes":[{"Phoneme":"s","AccuracyScore":100.0,"Offset":67000000,"Duration":700000},
      {"Phoneme":"ow","AccuracyScore":100.0,"Offset":67800000,"Duration":900000},{"Phoneme":"sh","AccuracyScore":100.0,"Offset":68800000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":69400000,"Duration":700000},{"Phoneme":"l","AccuracyScore":100.0,
      "Offset":70200000,"Duration":600000}]},{"Word":"platforms","AccuracyScore":100.0,"ErrorType":"None","Offset":70900000,"Duration":7200000,"Phonemes":[{"Phoneme":"p","AccuracyScore":100.0,"Offset":70900000,"Duration":600000},{"Phoneme":"l","AccuracyScore":100.0,
      "Offset":71600000,"Duration":500000},{"Phoneme":"ae","AccuracyScore":100.0,"Offset":72200000,"Duration":500000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":72800000,"Duration":800000},{"Phoneme":"f","AccuracyScore":100.0,"Offset":73700000,"Duration":600000},
      {"Phoneme":"ao","AccuracyScore":100.0,"Offset":74400000,"Duration":300000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":74800000,"Duration":700000},{"Phoneme":"m","AccuracyScore":100.0,"Offset":75600000,"Duration":700000},{"Phoneme":"z","AccuracyScore":99.0,
      "Offset":76400000,"Duration":1700000}]},{"Word":"like","AccuracyScore":90.0,"ErrorType":"None","Offset":84300000,"Duration":4300000,"Phonemes":[{"Phoneme":"l","AccuracyScore":100.0,"Offset":84300000,"Duration":1800000},{"Phoneme":"ay","AccuracyScore":100.0,"Offset":86200000,"Duration":700000},{"Phoneme":"k","AccuracyScore":75.0,"Offset":87000000,"Duration":1600000}]},{"Word":"facebook","AccuracyScore":84.0,"ErrorType":"None","Offset":89500000,"Duration":6000000,"Phonemes":[{"Phoneme":"f","AccuracyScore":70.0,"Offset":89500000,"Duration":1400000},{"Phoneme":"ey","AccuracyScore":50.0,"Offset":91000000,"Duration":900000},{"Phoneme":"s","AccuracyScore":100.0,"Offset":92000000,"Duration":700000},{"Phoneme":"b","AccuracyScore":100.0,"Offset":92800000,"Duration":900000},{"Phoneme":"uh","AccuracyScore":100.0,"Offset":93800000,"Duration":500000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":94400000,"Duration":1100000}]},{"Word":"twitter","AccuracyScore":100.0,"ErrorType":"None","Offset":95600000,"Duration":3900000,"Phonemes":[{"Phoneme":"t","AccuracyScore":100.0,"Offset":95600000,"Duration":700000},{"Phoneme":"w","AccuracyScore":100.0,"Offset":96400000,"Duration":300000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":96800000,"Duration":500000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":97400000,"Duration":600000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":98100000,"Duration":600000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":98800000,"Duration":700000}]},{"Word":"and","AccuracyScore":100.0,"ErrorType":"None","Offset":99600000,"Duration":1300000,"Phonemes":[{"Phoneme":"ae","AccuracyScore":73.0,"Offset":99600000,"Duration":700000},{"Phoneme":"n","AccuracyScore":100.0,"Offset":100400000,"Duration":500000}]},{"Word":"linkedin","AccuracyScore":87.0,"ErrorType":"None","Offset":101000000,"Duration":6100000,"Phonemes":[{"Phoneme":"l","AccuracyScore":100.0,"Offset":101000000,"Duration":600000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":101700000,"Duration":400000},{"Phoneme":"ng","AccuracyScore":100.0,"Offset":102200000,"Duration":500000},{"Phoneme":"k","AccuracyScore":90.0,"Offset":102800000,"Duration":200000},{"Phoneme":"t","AccuracyScore":98.0,"Offset":103100000,"Duration":400000},{"Phoneme":"ih","AccuracyScore":86.0,"Offset":103600000,"Duration":500000},{"Phoneme":"n","AccuracyScore":77.0,"Offset":104200000,"Duration":2900000}]},{"Word":"you","AccuracyScore":100.0,"ErrorType":"None","Offset":107400000,"Duration":1300000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":107400000,"Duration":600000},{"Phoneme":"uw","AccuracyScore":100.0,"Offset":108100000,"Duration":600000}]},{"Word":"need","AccuracyScore":100.0,"ErrorType":"None","Offset":108800000,"Duration":2500000,"Phonemes":[{"Phoneme":"n","AccuracyScore":100.0,"Offset":108800000,"Duration":900000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":109800000,"Duration":500000},{"Phoneme":"d","AccuracyScore":100.0,"Offset":110400000,"Duration":900000}]},{"Word":"to","AccuracyScore":100.0,"ErrorType":"None","Offset":111400000,"Duration":1100000,"Phonemes":[{"Phoneme":"t","AccuracyScore":100.0,"Offset":111400000,"Duration":500000},{"Phoneme":"uh","AccuracyScore":62.0,"Offset":112000000,"Duration":500000}]},{"Word":"rethink","AccuracyScore":100.0,"ErrorType":"None","Offset":112600000,"Duration":3700000,"Phonemes":[{"Phoneme":"r","AccuracyScore":100.0,"Offset":112600000,"Duration":900000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":113600000,"Duration":500000},{"Phoneme":"th","AccuracyScore":100.0,"Offset":114200000,"Duration":900000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":115200000,"Duration":300000},{"Phoneme":"ng","AccuracyScore":100.0,"Offset":115600000,"Duration":300000},{"Phoneme":"k","AccuracyScore":96.0,"Offset":116000000,"Duration":300000}]},{"Word":"your","AccuracyScore":91.0,"ErrorType":"None","Offset":116400000,"Duration":1000000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":116400000,"Duration":200000},{"Phoneme":"ao","AccuracyScore":1.0,"Offset":116700000,"Duration":300000},{"Phoneme":"r","AccuracyScore":86.0,"Offset":117100000,"Duration":300000}]},{"Word":"strategy","AccuracyScore":96.0,"ErrorType":"None","Offset":117500000,"Duration":6600000,"Phonemes":[{"Phoneme":"s","AccuracyScore":83.0,"Offset":117500000,"Duration":300000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":117900000,"Duration":600000},
      {"Phoneme":"r","AccuracyScore":100.0,"Offset":118600000,"Duration":500000},{"Phoneme":"ae","AccuracyScore":100.0,"Offset":119200000,"Duration":200000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":119500000,"Duration":600000},{"Phoneme":"ax","AccuracyScore":100.0,
      "Offset":120200000,"Duration":500000},{"Phoneme":"jh","AccuracyScore":100.0,"Offset":120800000,"Duration":500000},{"Phoneme":"iy","AccuracyScore":94.0,"Offset":121400000,"Duration":2700000}]}]}]}
    
    this.beforeScore = bs.NBest.find(n => n);

    const as = {"RecognitionStatus":"Success","Offset":200000,"Duration":147000000,"NBest":[{"AccuracyScore":90.0,"FluencyScore":95.0,"CompletenessScore":100.0,"PronScore":93.0,"Words":[{"Word":"your","AccuracyScore":100.0,"ErrorType":"None","Offset":400000,"Duration":2500000,"Phonemes":[{"Phoneme":"y","AccuracyScore":99.0,"Offset":400000,"Duration":1100000},{"Phoneme":"ao","AccuracyScore":63.0,"Offset":1600000,"Duration":700000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":2400000,"Duration":500000}]},{"Word":"customers","AccuracyScore":100.0,"ErrorType":"None","Offset":3000000,"Duration":6100000,"Phonemes":[{"Phoneme":"k","AccuracyScore":100.0,"Offset":3000000,"Duration":700000},{"Phoneme":"ah","AccuracyScore":100.0,"Offset":3800000,"Duration":500000},{"Phoneme":"s","AccuracyScore":100.0,"Offset":4400000,"Duration":700000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":5200000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":5800000,"Duration":500000},{"Phoneme":"m","AccuracyScore":100.0,"Offset":6400000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":7000000,"Duration":700000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":7800000,"Duration":500000},{"Phoneme":"z","AccuracyScore":100.0,"Offset":8400000,"Duration":700000}]},{"Word":"are","AccuracyScore":100.0,"ErrorType":"None","Offset":9200000,"Duration":1500000,"Phonemes":[{"Phoneme":"aa","AccuracyScore":100.0,"Offset":9200000,"Duration":700000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":10000000,"Duration":700000}]},{"Word":"likely","AccuracyScore":100.0,"ErrorType":"None","Offset":10800000,"Duration":5500000,"Phonemes":[{"Phoneme":"l","AccuracyScore":100.0,"Offset":10800000,"Duration":900000},{"Phoneme":"ay","AccuracyScore":100.0,"Offset":11800000,"Duration":1100000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":13000000,"Duration":900000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":14000000,"Duration":700000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":14800000,"Duration":1500000}]},{"Word":"already","AccuracyScore":77.0,"ErrorType":"None","Offset":16400000,"Duration":6500000,"Phonemes":[{"Phoneme":"ao","AccuracyScore":100.0,"Offset":16400000,"Duration":1500000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":18000000,"Duration":1300000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":19400000,"Duration":300000},{"Phoneme":"eh","AccuracyScore":100.0,"Offset":19800000,"Duration":300000},{"Phoneme":"d","AccuracyScore":91.0,"Offset":20200000,"Duration":1200000},{"Phoneme":"iy","AccuracyScore":6.0,"Offset":21500000,"Duration":1400000}]},{"Word":"attracting","AccuracyScore":83.0,"ErrorType":"None","Offset":23000000,"Duration":6700000,"Phonemes":[{"Phoneme":"ax","AccuracyScore":0.0,"Offset":23000000,"Duration":300000},{"Phoneme":"t","AccuracyScore":45.0,"Offset":23400000,"Duration":1300000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":24800000,"Duration":500000},{"Phoneme":"ae","AccuracyScore":100.0,"Offset":25400000,"Duration":500000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":26000000,"Duration":900000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":27000000,"Duration":500000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":27600000,"Duration":700000},{"Phoneme":"ng","AccuracyScore":100.0,"Offset":28400000,"Duration":1300000}]},{"Word":"with","AccuracyScore":100.0,"ErrorType":"None","Offset":29800000,"Duration":2900000,"Phonemes":[{"Phoneme":"w","AccuracyScore":100.0,"Offset":29800000,"Duration":700000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":30600000,"Duration":300000},{"Phoneme":"th","AccuracyScore":4.0,"Offset":31000000,"Duration":1700000}]},{"Word":"clients","AccuracyScore":43.0,"ErrorType":"None","Offset":32800000,"Duration":7900000,"Phonemes":[{"Phoneme":"k","AccuracyScore":7.0,"Offset":32800000,"Duration":700000},{"Phoneme":"l","AccuracyScore":0.0,"Offset":33600000,"Duration":500000},{"Phoneme":"ay","AccuracyScore":55.0,"Offset":34200000,"Duration":1000000},{"Phoneme":"ax","AccuracyScore":59.0,"Offset":35300000,"Duration":900000},{"Phoneme":"n","AccuracyScore":1.0,"Offset":36300000,"Duration":200000},{"Phoneme":"t","AccuracyScore":71.0,"Offset":36600000,"Duration":700000},{"Phoneme":"s","AccuracyScore":48.0,"Offset":37400000,"Duration":3300000}]},{"Word":"through","AccuracyScore":100.0,"ErrorType":"None","Offset":41000000,"Duration":2900000,"Phonemes":[{"Phoneme":"th","AccuracyScore":100.0,"Offset":41000000,"Duration":1500000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":42600000,"Duration":500000},{"Phoneme":"uw","AccuracyScore":100.0,"Offset":43200000,"Duration":700000}]},{"Word":"social","AccuracyScore":100.0,"ErrorType":"None","Offset":44000000,"Duration":3900000,"Phonemes":[{"Phoneme":"s","AccuracyScore":100.0,"Offset":44000000,"Duration":800000},{"Phoneme":"ow","AccuracyScore":100.0,"Offset":44900000,"Duration":800000},{"Phoneme":"sh","AccuracyScore":100.0,"Offset":45800000,"Duration":700000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":46600000,"Duration":600000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":47300000,"Duration":600000}]},{"Word":"media","AccuracyScore":100.0,"ErrorType":"None","Offset":48000000,"Duration":5400000,"Phonemes":[{"Phoneme":"m","AccuracyScore":100.0,"Offset":48000000,"Duration":500000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":48600000,"Duration":500000},{"Phoneme":"d","AccuracyScore":100.0,"Offset":49200000,"Duration":600000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":49900000,"Duration":600000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":50600000,"Duration":2800000}]},{"Word":"if","AccuracyScore":100.0,"ErrorType":"None","Offset":57400000,"Duration":2300000,"Phonemes":[{"Phoneme":"ih","AccuracyScore":100.0,"Offset":57400000,"Duration":1700000},{"Phoneme":"f","AccuracyScore":100.0,"Offset":59200000,"Duration":500000}]},{"Word":"you","AccuracyScore":100.0,"ErrorType":"None","Offset":59800000,"Duration":1500000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":59800000,"Duration":700000},{"Phoneme":"uw","AccuracyScore":100.0,"Offset":60600000,"Duration":700000}]},{"Word":"aren't","AccuracyScore":84.0,"ErrorType":"None","Offset":61400000,"Duration":4100000,"Phonemes":[{"Phoneme":"aa","AccuracyScore":100.0,"Offset":61400000,"Duration":1400000},{"Phoneme":"r","AccuracyScore":56.0,"Offset":62900000,"Duration":1200000},{"Phoneme":"n","AccuracyScore":85.0,"Offset":64200000,"Duration":600000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":64900000,"Duration":600000}]},{"Word":"speaking","AccuracyScore":79.0,"ErrorType":"None","Offset":65600000,"Duration":5500000,"Phonemes":[{"Phoneme":"s","AccuracyScore":98.0,"Offset":65600000,"Duration":500000},{"Phoneme":"p","AccuracyScore":100.0,"Offset":66200000,"Duration":900000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":67200000,"Duration":900000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":68200000,"Duration":900000},{"Phoneme":"ih","AccuracyScore":52.0,"Offset":69200000,"Duration":1500000},{"Phoneme":"ng","AccuracyScore":0.0,"Offset":70800000,"Duration":300000}]},{"Word":"to","AccuracyScore":40.0,"ErrorType":"None","Offset":71200000,"Duration":600000,"Phonemes":[{"Phoneme":"t","AccuracyScore":40.0,"Offset":71200000,"Duration":300000},{"Phoneme":"uh","AccuracyScore":0.0,"Offset":71600000,"Duration":200000}]},{"Word":"your","AccuracyScore":45.0,"ErrorType":"None","Offset":71900000,"Duration":2800000,"Phonemes":[{"Phoneme":"y","AccuracyScore":0.0,"Offset":71900000,"Duration":1500000},{"Phoneme":"ao","AccuracyScore":80.0,"Offset":73500000,"Duration":600000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":74200000,"Duration":500000}]},{"Word":"customers","AccuracyScore":100.0,"ErrorType":"None","Offset":74800000,"Duration":6700000,"Phonemes":[{"Phoneme":"k","AccuracyScore":100.0,"Offset":74800000,"Duration":700000},{"Phoneme":"ah","AccuracyScore":100.0,"Offset":75600000,"Duration":600000},{"Phoneme":"s","AccuracyScore":100.0,"Offset":76300000,"Duration":400000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":76800000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":77400000,"Duration":700000},{"Phoneme":"m","AccuracyScore":100.0,"Offset":78200000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":78800000,"Duration":900000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":79800000,"Duration":500000},{"Phoneme":"z","AccuracyScore":100.0,"Offset":80400000,"Duration":1100000}]},{"Word":"through","AccuracyScore":100.0,"ErrorType":"None","Offset":81600000,"Duration":2700000,"Phonemes":[{"Phoneme":"th","AccuracyScore":100.0,"Offset":81600000,"Duration":1300000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":83000000,"Duration":500000},{"Phoneme":"uw","AccuracyScore":100.0,"Offset":83600000,"Duration":700000}]},{"Word":"social","AccuracyScore":100.0,"ErrorType":"None","Offset":84400000,"Duration":4600000,"Phonemes":[{"Phoneme":"s","AccuracyScore":100.0,"Offset":84400000,"Duration":900000},{"Phoneme":"ow","AccuracyScore":100.0,"Offset":85400000,"Duration":1100000},{"Phoneme":"sh","AccuracyScore":100.0,"Offset":86600000,"Duration":900000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":87600000,"Duration":700000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":88400000,"Duration":600000}]},{"Word":"platforms","AccuracyScore":100.0,"ErrorType":"None","Offset":89100000,"Duration":6000000,"Phonemes":[{"Phoneme":"p","AccuracyScore":100.0,"Offset":89100000,"Duration":500000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":89700000,"Duration":600000},{"Phoneme":"ae","AccuracyScore":100.0,"Offset":90400000,"Duration":500000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":91000000,"Duration":900000},{"Phoneme":"f","AccuracyScore":100.0,"Offset":92000000,"Duration":500000},{"Phoneme":"ao","AccuracyScore":100.0,"Offset":92600000,"Duration":300000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":93000000,"Duration":500000},{"Phoneme":"m","AccuracyScore":100.0,"Offset":93600000,"Duration":700000},{"Phoneme":"z","AccuracyScore":100.0,"Offset":94400000,"Duration":700000}]},{"Word":"like","AccuracyScore":61.0,"ErrorType":"None","Offset":95200000,"Duration":2500000,"Phonemes":[{"Phoneme":"l","AccuracyScore":86.0,"Offset":95200000,"Duration":700000},{"Phoneme":"ay","AccuracyScore":37.0,"Offset":96000000,"Duration":700000},{"Phoneme":"k","AccuracyScore":59.0,"Offset":96800000,"Duration":900000}]},{"Word":"facebook","AccuracyScore":89.0,"ErrorType":"None","Offset":97800000,"Duration":8500000,"Phonemes":[{"Phoneme":"f","AccuracyScore":100.0,"Offset":97800000,"Duration":700000},{"Phoneme":"ey","AccuracyScore":100.0,"Offset":98600000,"Duration":800000},{"Phoneme":"s","AccuracyScore":100.0,"Offset":99500000,"Duration":800000},{"Phoneme":"b","AccuracyScore":100.0,"Offset":100400000,"Duration":900000},{"Phoneme":"uh","AccuracyScore":100.0,"Offset":101400000,"Duration":700000},{"Phoneme":"k","AccuracyScore":78.0,"Offset":102200000,"Duration":4100000}]},{"Word":"twitter","AccuracyScore":89.0,"ErrorType":"None","Offset":106600000,"Duration":7400000,"Phonemes":[{"Phoneme":"t","AccuracyScore":100.0,"Offset":106600000,"Duration":1300000},{"Phoneme":"w","AccuracyScore":100.0,"Offset":108000000,"Duration":300000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":108400000,"Duration":500000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":109000000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":109600000,"Duration":900000},{"Phoneme":"r","AccuracyScore":77.0,"Offset":110600000,"Duration":3400000}]},{"Word":"and","AccuracyScore":100.0,"ErrorType":"None","Offset":114900000,"Duration":2600000,"Phonemes":[{"Phoneme":"ae","AccuracyScore":97.0,"Offset":114900000,"Duration":1600000},{"Phoneme":"n","AccuracyScore":100.0,"Offset":116600000,"Duration":900000}]},{"Word":"linkedin","AccuracyScore":95.0,"ErrorType":"None","Offset":117600000,"Duration":6900000,"Phonemes":[{"Phoneme":"l","AccuracyScore":100.0,"Offset":117600000,"Duration":700000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":118400000,"Duration":700000},{"Phoneme":"ng","AccuracyScore":100.0,"Offset":119200000,"Duration":300000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":119600000,"Duration":500000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":120200000,"Duration":500000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":120800000,"Duration":700000},{"Phoneme":"n","AccuracyScore":89.0,"Offset":121600000,"Duration":2900000}]},{"Word":"you","AccuracyScore":100.0,"ErrorType":"None","Offset":127100000,"Duration":2200000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":127100000,"Duration":1200000},{"Phoneme":"uw","AccuracyScore":100.0,"Offset":128400000,"Duration":900000}]},{"Word":"need","AccuracyScore":100.0,"ErrorType":"None","Offset":129400000,"Duration":2500000,"Phonemes":[{"Phoneme":"n","AccuracyScore":100.0,"Offset":129400000,"Duration":1100000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":130600000,"Duration":600000},{"Phoneme":"d","AccuracyScore":100.0,"Offset":131300000,"Duration":600000}]},{"Word":"to","AccuracyScore":100.0,"ErrorType":"None","Offset":132000000,"Duration":1300000,"Phonemes":[{"Phoneme":"t","AccuracyScore":100.0,"Offset":132000000,"Duration":500000},{"Phoneme":"uh","AccuracyScore":21.0,"Offset":132600000,"Duration":700000}]},{"Word":"rethink","AccuracyScore":99.0,"ErrorType":"None","Offset":133400000,"Duration":4700000,"Phonemes":[{"Phoneme":"r","AccuracyScore":100.0,"Offset":133400000,"Duration":900000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":134400000,"Duration":900000},{"Phoneme":"th","AccuracyScore":98.0,"Offset":135400000,"Duration":900000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":136400000,"Duration":600000},{"Phoneme":"ng","AccuracyScore":99.0,"Offset":137100000,"Duration":400000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":137600000,"Duration":500000}]},{"Word":"your","AccuracyScore":90.0,"ErrorType":"None","Offset":138200000,"Duration":1400000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":138200000,"Duration":300000},{"Phoneme":"ao","AccuracyScore":1.0,"Offset":138600000,"Duration":600000},{"Phoneme":"r","AccuracyScore":78.0,"Offset":139300000,"Duration":300000}]},{"Word":"strategy","AccuracyScore":99.0,"ErrorType":"None","Offset":139700000,"Duration":7200000,"Phonemes":[{"Phoneme":"s","AccuracyScore":88.0,"Offset":139700000,"Duration":400000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":140200000,"Duration":700000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":141000000,"Duration":500000},{"Phoneme":"ae","AccuracyScore":100.0,"Offset":141600000,"Duration":400000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":142100000,"Duration":800000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":143000000,"Duration":500000},{"Phoneme":"jh","AccuracyScore":100.0,"Offset":143600000,"Duration":700000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":144400000,"Duration":2500000}]}]}]}
    this.afterScore = as.NBest.find(n => n);

    const ms = {"RecognitionStatus":"Success","Offset":8400000,"Duration":130900000,"NBest":[{"AccuracyScore":100.0,"FluencyScore":98.0,"CompletenessScore":100.0,"PronScore":98.8,"Words":[{"Word":"your","AccuracyScore":98.0,"ErrorType":"None","Offset":8600000,"Duration":2500000,"Phonemes":[{"Phoneme":"y","AccuracyScore":96.0,"Offset":8600000,"Duration":1300000},{"Phoneme":"ao","AccuracyScore":1.0,"Offset":10000000,"Duration":500000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":10600000,"Duration":500000}]},{"Word":"customers","AccuracyScore":100.0,"ErrorType":"None","Offset":11200000,"Duration":6300000,"Phonemes":[{"Phoneme":"k","AccuracyScore":100.0,"Offset":11200000,"Duration":700000},{"Phoneme":"ah","AccuracyScore":100.0,"Offset":12000000,"Duration":1100000},{"Phoneme":"s","AccuracyScore":100.0,"Offset":13200000,"Duration":500000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":13800000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":14400000,"Duration":300000},{"Phoneme":"m","AccuracyScore":100.0,"Offset":14800000,"Duration":300000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":15200000,"Duration":900000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":16200000,"Duration":500000},{"Phoneme":"z","AccuracyScore":100.0,"Offset":16800000,"Duration":700000}]},{"Word":"are","AccuracyScore":100.0,"ErrorType":"None","Offset":17600000,"Duration":1500000,"Phonemes":[{"Phoneme":"aa","AccuracyScore":100.0,"Offset":17600000,"Duration":800000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":18500000,"Duration":600000}]},{"Word":"likely","AccuracyScore":100.0,"ErrorType":"None","Offset":19200000,"Duration":4500000,"Phonemes":[{"Phoneme":"l","AccuracyScore":100.0,"Offset":19200000,"Duration":1300000},{"Phoneme":"ay","AccuracyScore":100.0,"Offset":20600000,"Duration":700000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":21400000,"Duration":700000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":22200000,"Duration":700000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":23000000,"Duration":700000}]},{"Word":"already","AccuracyScore":100.0,"ErrorType":"None","Offset":23800000,"Duration":4200000,"Phonemes":[{"Phoneme":"ao","AccuracyScore":100.0,"Offset":23800000,"Duration":500000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":24400000,"Duration":700000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":25200000,"Duration":700000},{"Phoneme":"eh","AccuracyScore":100.0,"Offset":26000000,"Duration":500000},{"Phoneme":"d","AccuracyScore":100.0,"Offset":26600000,"Duration":700000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":27400000,"Duration":600000}]},{"Word":"attracting","AccuracyScore":100.0,"ErrorType":"None","Offset":28100000,"Duration":8200000,"Phonemes":[{"Phoneme":"ax","AccuracyScore":100.0,"Offset":28100000,"Duration":1000000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":29200000,"Duration":1300000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":30600000,"Duration":900000},{"Phoneme":"ae","AccuracyScore":100.0,"Offset":31600000,"Duration":700000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":32400000,"Duration":900000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":33400000,"Duration":500000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":34000000,"Duration":900000},{"Phoneme":"ng","AccuracyScore":100.0,"Offset":35000000,"Duration":1300000}]},{"Word":"with","AccuracyScore":100.0,"ErrorType":"None","Offset":36400000,"Duration":2300000,"Phonemes":[{"Phoneme":"w","AccuracyScore":100.0,"Offset":36400000,"Duration":900000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":37400000,"Duration":700000},{"Phoneme":"th","AccuracyScore":36.0,"Offset":38200000,"Duration":500000}]},{"Word":"clients","AccuracyScore":100.0,"ErrorType":"None","Offset":38800000,"Duration":6700000,"Phonemes":[{"Phoneme":"k","AccuracyScore":100.0,"Offset":38800000,"Duration":1300000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":40200000,"Duration":900000},{"Phoneme":"ay","AccuracyScore":100.0,"Offset":41200000,"Duration":900000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":42200000,"Duration":1200000},{"Phoneme":"n","AccuracyScore":100.0,"Offset":43500000,"Duration":300000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":43900000,"Duration":800000},{"Phoneme":"s","AccuracyScore":100.0,"Offset":44800000,"Duration":700000}]},{"Word":"through","AccuracyScore":100.0,"ErrorType":"None","Offset":45600000,"Duration":2500000,"Phonemes":[{"Phoneme":"th","AccuracyScore":100.0,"Offset":45600000,"Duration":1100000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":46800000,"Duration":500000},{"Phoneme":"uw","AccuracyScore":100.0,"Offset":47400000,"Duration":700000}]},{"Word":"social","AccuracyScore":100.0,"ErrorType":"None","Offset":48200000,"Duration":3700000,"Phonemes":[{"Phoneme":"s","AccuracyScore":100.0,"Offset":48200000,"Duration":700000},{"Phoneme":"ow","AccuracyScore":100.0,"Offset":49000000,"Duration":1300000},{"Phoneme":"sh","AccuracyScore":100.0,"Offset":50400000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":51000000,"Duration":500000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":51600000,"Duration":300000}]},{"Word":"media","AccuracyScore":100.0,"ErrorType":"None","Offset":52000000,"Duration":4900000,"Phonemes":[{"Phoneme":"m","AccuracyScore":100.0,"Offset":52000000,"Duration":700000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":52800000,"Duration":500000},{"Phoneme":"d","AccuracyScore":100.0,"Offset":53400000,"Duration":700000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":54200000,"Duration":700000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":55000000,"Duration":1900000}]},{"Word":"if","AccuracyScore":100.0,"ErrorType":"None","Offset":58900000,"Duration":2100000,"Phonemes":[{"Phoneme":"ih","AccuracyScore":100.0,"Offset":58900000,"Duration":1600000},{"Phoneme":"f","AccuracyScore":100.0,"Offset":60600000,"Duration":400000}]},{"Word":"you","AccuracyScore":100.0,"ErrorType":"None","Offset":61100000,"Duration":1400000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":61100000,"Duration":400000},{"Phoneme":"uw","AccuracyScore":87.0,"Offset":61600000,"Duration":900000}]},{"Word":"aren't","AccuracyScore":100.0,"ErrorType":"None","Offset":62600000,"Duration":3700000,"Phonemes":[{"Phoneme":"aa","AccuracyScore":100.0,"Offset":62600000,"Duration":1300000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":64000000,"Duration":900000},{"Phoneme":"n","AccuracyScore":100.0,"Offset":65000000,"Duration":500000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":65600000,"Duration":700000}]},{"Word":"speaking","AccuracyScore":100.0,"ErrorType":"None","Offset":66400000,"Duration":4700000,"Phonemes":[{"Phoneme":"s","AccuracyScore":100.0,"Offset":66400000,"Duration":700000},{"Phoneme":"p","AccuracyScore":100.0,"Offset":67200000,"Duration":1100000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":68400000,"Duration":700000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":69200000,"Duration":700000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":70000000,"Duration":500000},{"Phoneme":"ng","AccuracyScore":100.0,"Offset":70600000,"Duration":500000}]},{"Word":"to","AccuracyScore":100.0,"ErrorType":"None","Offset":71200000,"Duration":700000,"Phonemes":[{"Phoneme":"t","AccuracyScore":100.0,"Offset":71200000,"Duration":300000},{"Phoneme":"uh","AccuracyScore":0.0,"Offset":71600000,"Duration":300000}]},{"Word":"your","AccuracyScore":100.0,"ErrorType":"None","Offset":72000000,"Duration":1300000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":72000000,"Duration":300000},{"Phoneme":"ao","AccuracyScore":0.0,"Offset":72400000,"Duration":400000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":72900000,"Duration":400000}]},{"Word":"customers","AccuracyScore":98.0,"ErrorType":"None","Offset":73400000,"Duration":7500000,"Phonemes":[{"Phoneme":"k","AccuracyScore":100.0,"Offset":73400000,"Duration":700000},{"Phoneme":"ah","AccuracyScore":100.0,"Offset":74200000,"Duration":900000},{"Phoneme":"s","AccuracyScore":100.0,"Offset":75200000,"Duration":700000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":76000000,"Duration":300000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":76400000,"Duration":300000},{"Phoneme":"m","AccuracyScore":100.0,"Offset":76800000,"Duration":300000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":77200000,"Duration":700000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":78000000,"Duration":700000},{"Phoneme":"z","AccuracyScore":94.0,"Offset":78800000,"Duration":2100000}]},{"Word":"through","AccuracyScore":100.0,"ErrorType":"None","Offset":81200000,"Duration":4300000,"Phonemes":[{"Phoneme":"th","AccuracyScore":100.0,"Offset":81200000,"Duration":2300000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":83600000,"Duration":700000},{"Phoneme":"uw","AccuracyScore":100.0,"Offset":84400000,"Duration":1100000}]},{"Word":"social","AccuracyScore":100.0,"ErrorType":"None","Offset":85600000,"Duration":4100000,"Phonemes":[{"Phoneme":"s","AccuracyScore":100.0,"Offset":85600000,"Duration":600000},{"Phoneme":"ow","AccuracyScore":100.0,"Offset":86300000,"Duration":1200000},{"Phoneme":"sh","AccuracyScore":100.0,"Offset":87600000,"Duration":700000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":88400000,"Duration":600000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":89100000,"Duration":600000}]},{"Word":"platforms","AccuracyScore":100.0,"ErrorType":"None","Offset":89800000,"Duration":5900000,"Phonemes":[{"Phoneme":"p","AccuracyScore":100.0,"Offset":89800000,"Duration":500000},{"Phoneme":"l","AccuracyScore":100.0,"Offset":90400000,"Duration":700000},{"Phoneme":"ae","AccuracyScore":100.0,"Offset":91200000,"Duration":500000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":91800000,"Duration":600000},{"Phoneme":"f","AccuracyScore":100.0,"Offset":92500000,"Duration":600000},{"Phoneme":"ao","AccuracyScore":100.0,"Offset":93200000,"Duration":400000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":93700000,"Duration":700000},{"Phoneme":"m","AccuracyScore":100.0,"Offset":94500000,"Duration":600000},{"Phoneme":"z","AccuracyScore":100.0,"Offset":95200000,"Duration":500000}]},{"Word":"like","AccuracyScore":100.0,"ErrorType":"None","Offset":95800000,"Duration":2700000,"Phonemes":[{"Phoneme":"l","AccuracyScore":100.0,"Offset":95800000,"Duration":700000},{"Phoneme":"ay","AccuracyScore":100.0,"Offset":96600000,"Duration":700000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":97400000,"Duration":1100000}]},{"Word":"facebook","AccuracyScore":97.0,"ErrorType":"None","Offset":98600000,"Duration":7100000,"Phonemes":[{"Phoneme":"f","AccuracyScore":100.0,"Offset":98600000,"Duration":900000},{"Phoneme":"ey","AccuracyScore":100.0,"Offset":99600000,"Duration":900000},{"Phoneme":"s","AccuracyScore":100.0,"Offset":100600000,"Duration":700000},{"Phoneme":"b","AccuracyScore":100.0,"Offset":101400000,"Duration":900000},{"Phoneme":"uh","AccuracyScore":100.0,"Offset":102400000,"Duration":1100000},{"Phoneme":"k","AccuracyScore":90.0,"Offset":103600000,"Duration":2100000}]},{"Word":"twitter","AccuracyScore":100.0,"ErrorType":"None","Offset":106000000,"Duration":3900000,"Phonemes":[{"Phoneme":"t","AccuracyScore":100.0,"Offset":106000000,"Duration":1600000},{"Phoneme":"w","AccuracyScore":100.0,"Offset":107700000,"Duration":400000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":108200000,"Duration":500000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":108800000,"Duration":300000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":109200000,"Duration":300000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":109600000,"Duration":300000}]},{"Word":"and","AccuracyScore":100.0,"ErrorType":"None","Offset":110000000,"Duration":900000,"Phonemes":[{"Phoneme":"ae","AccuracyScore":1.0,"Offset":110000000,"Duration":500000},{"Phoneme":"n","AccuracyScore":100.0,"Offset":110600000,"Duration":300000}]},{"Word":"linkedin","AccuracyScore":100.0,"ErrorType":"None","Offset":111000000,"Duration":6500000,"Phonemes":[{"Phoneme":"l","AccuracyScore":100.0,"Offset":111000000,"Duration":500000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":111600000,"Duration":500000},{"Phoneme":"ng","AccuracyScore":100.0,"Offset":112200000,"Duration":300000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":112600000,"Duration":500000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":113200000,"Duration":500000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":113800000,"Duration":1300000},{"Phoneme":"n","AccuracyScore":100.0,"Offset":115200000,"Duration":2300000}]},{"Word":"you","AccuracyScore":100.0,"ErrorType":"None","Offset":117800000,"Duration":2700000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":117800000,"Duration":1900000},{"Phoneme":"uw","AccuracyScore":100.0,"Offset":119800000,"Duration":700000}]},{"Word":"need","AccuracyScore":100.0,"ErrorType":"None","Offset":120600000,"Duration":2600000,"Phonemes":[{"Phoneme":"n","AccuracyScore":100.0,"Offset":120600000,"Duration":1100000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":121800000,"Duration":700000},{"Phoneme":"d","AccuracyScore":100.0,"Offset":122600000,"Duration":600000}]},{"Word":"to","AccuracyScore":100.0,"ErrorType":"None","Offset":123300000,"Duration":1000000,"Phonemes":[{"Phoneme":"t","AccuracyScore":100.0,"Offset":123300000,"Duration":400000},{"Phoneme":"uh","AccuracyScore":79.0,"Offset":123800000,"Duration":500000}]},{"Word":"rethink","AccuracyScore":100.0,"ErrorType":"None","Offset":124400000,"Duration":4500000,"Phonemes":[{"Phoneme":"r","AccuracyScore":100.0,"Offset":124400000,"Duration":500000},{"Phoneme":"iy","AccuracyScore":100.0,"Offset":125000000,"Duration":900000},{"Phoneme":"th","AccuracyScore":100.0,"Offset":126000000,"Duration":700000},{"Phoneme":"ih","AccuracyScore":100.0,"Offset":126800000,"Duration":700000},{"Phoneme":"ng","AccuracyScore":100.0,"Offset":127600000,"Duration":700000},{"Phoneme":"k","AccuracyScore":100.0,"Offset":128400000,"Duration":500000}]},{"Word":"your","AccuracyScore":100.0,"ErrorType":"None","Offset":129000000,"Duration":1300000,"Phonemes":[{"Phoneme":"y","AccuracyScore":100.0,"Offset":129000000,"Duration":300000},{"Phoneme":"ao","AccuracyScore":0.0,"Offset":129400000,"Duration":300000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":129800000,"Duration":500000}]},{"Word":"strategy","AccuracyScore":96.0,"ErrorType":"None","Offset":130400000,"Duration":7500000,"Phonemes":[{"Phoneme":"s","AccuracyScore":100.0,"Offset":130400000,"Duration":300000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":130800000,"Duration":800000},{"Phoneme":"r","AccuracyScore":100.0,"Offset":131700000,"Duration":600000},{"Phoneme":"ae","AccuracyScore":100.0,"Offset":132400000,"Duration":300000},{"Phoneme":"t","AccuracyScore":100.0,"Offset":132800000,"Duration":500000},{"Phoneme":"ax","AccuracyScore":100.0,"Offset":133400000,"Duration":500000},{"Phoneme":"jh","AccuracyScore":100.0,"Offset":134000000,"Duration":700000},{"Phoneme":"iy","AccuracyScore":91.0,"Offset":134800000,"Duration":3100000}]}]}]}
    this.myScore = ms.NBest.find(n => n);

    console.table(this.afterScore)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
