<template>
  <section class="pt-2">
    <nuxt-link to="/" class="p-3">
      <b-icon icon="box-arrow-left" scale="2"></b-icon>
    </nuxt-link>
    <section class="container">
      <div class="text-2xl">日本史年表</div>
      <!-- ステップ
      <select v-model="step" class="form-control w-auto">
        <option value="10">10</option>
        <option value="25">25</option>
        <option value="50">50</option>
        <option value="100">100</option>
      </select> -->
      <!-- テーブル -->
      <section class="mh-80">
        <table class="table table-sm chronology">
          <thead class="table-info sticky-top">
            <th class="col-1 nowrap">年代</th>
            <th class="col-1 nowrap">時代</th>
            <th></th>
            <!-- <th class="">年</th>
            <th class="col-2">人物</th>
            <th>イベント</th> -->
          </thead>
          <tbody>
            <tr v-for="y in year" :key="y">
              <th class="text-right table-info">{{ y }}</th>
              <td>{{ period(y) }}</td>
              <td>
                <table class="table table-sm table-borderless mb-0">
                  <tr
                    v-for="(e, i) in jEvent"
                    :key="i"
                    v-show="e.date >= y && e.date < y + step"
                  >
                    <td class="col-2 nowrap">{{ e.date }}</td>
                    <td class="col-2 nowrap">{{ e.person }}</td>
                    <td>{{ e.event }}</td>
                  </tr>
                </table>
              </td>
              <!-- <td class="text-right">
                <ul>
                  <li
                    v-for="e in jEvent"
                    :key="e.date"
                    v-show="e.date >= y && e.date < y + step"
                  >
                    {{ e.date }}
                  </li>
                </ul>
              </td>
              <td>
                <ul>
                  <li
                    v-for="e in jEvent"
                    :key="e.date"
                    v-show="e.date >= y && e.date < y + step"
                  >
                    {{ e.person }}
                  </li>
                </ul>
              </td>
              <td>
                <ul>
                  <li
                    v-for="e in jEvent"
                    :key="e.date"
                    v-show="e.date >= y && e.date < y + step"
                  >
                    {{ e.event }}
                  </li>
                </ul>
              </td> -->
            </tr>
          </tbody>
        </table>
      </section>
    </section>
  </section>
</template>

<script>
import Vue from "vue";
import db from "../assets/db.json";

export default Vue.extend({
  data() {
    return {
      start: -500,
      last: 2100,
      step: 30,
      year: [],
      JapanPeriod: [
        { period: "縄文", from: -1000, to: -400 },
        { period: "弥生", from: -400, to: 250 },
        { period: "古墳", from: 250, to: 600 },
      ],
      jEvent: [
        {
          date: "57",
          person: "倭奴国王",
          event:
            "後漢に使いを送り、光武帝より「漢委奴国王」の金印を受け取る（志賀島出土金印）",
        },
        {
          date: "100",
          person: "",
          event: "青銅器と鉄がほぼ同時に伝わる",
        },
        {
          date: "189",
          person: "卑弥呼",
          event: "邪馬台国の女王となって統治",
        },
        {
          date: "239",
          person: "卑弥呼",
          event: "魏に使いを送り「親魏倭王」の号を受け取る",
        },
        {
          date: "350",
          person: "",
          event: "ヤマト政権成立　",
        },
        {
          date: "367",
          person: "",
          event: "百済の使者がくる",
        },
        {
          date: "369",
          person: "",
          event: "朝鮮半島に進出",
        },
        {
          date: "538",
          person: "",
          event: "仏教伝来(552年説あり)",
        },
        {
          date: "587",
          person: "蘇我馬子",
          event: "物部守屋を滅ぼす",
        },
        {
          date: "592",
          person: "蘇我馬子",
          event: "崇峻天皇を殺す",
        },
        {
          date: "593",
          person: "聖徳太子",
          event: "摂政政治",
        },
        {
          date: "594",
          person: "",
          event: "仏教興隆の詔",
        },
        {
          date: "603",
          person: "",
          event: "冠位十二階の制定",
        },
        {
          date: "604",
          person: "",
          event: "十七条の憲法の制定",
        },
        {
          date: "607",
          person: "",
          event: "敬神の詔",
        },
        {
          date: "607",
          person: "小野妹子",
          event: "遣隋使として隋に行く",
        },
        {
          date: "643",
          person: "蘇我入鹿",
          event: "山背大兄王とその一族を滅ぼす",
        },
        {
          date: "645",
          person: "",
          event: "蘇我氏が滅びる",
        },
        {
          date: "645",
          person: "",
          event: "大化の改新",
        },
        {
          date: "645",
          person: "",
          event: "天皇紀・国紀が焼失",
        },
        {
          date: "645",
          person: "",
          event: "戸籍を作らせる",
        },
        {
          date: "645",
          person: "",
          event: "仏教興隆の詔",
        },
        {
          date: "646",
          person: "",
          event: "改新の詔",
        },
        {
          date: "646",
          person: "",
          event: "公地公民制",
        },
        {
          date: "652",
          person: "",
          event: "班田収受法が施行",
        },
        {
          date: "658",
          person: "阿倍比羅夫",
          event: "蝦夷を打つ",
        },
        {
          date: "660",
          person: "中大兄皇子",
          event: "水時計を造る",
        },
        {
          date: "663",
          person: "",
          event: "白村江の戦い",
        },
        {
          date: "667",
          person: "",
          event: "近江大津京に遷都",
        },
        {
          date: "671",
          person: "",
          event: "水時計により鐘鼓を打って時刻を知らせ始める",
        },
        {
          date: "672",
          person: "",
          event: "壬申の乱、飛鳥京に遷都",
        },
        {
          date: "675",
          person: "",
          event: "占星台を設置",
        },
        {
          date: "684",
          person: "",
          event: "八色の姓を制定",
        },
        {
          date: "694",
          person: "",
          event: "藤原京に遷都",
        },
        {
          date: "701",
          person: "",
          event: "大宝律令ができる",
        },
        {
          date: "708",
          person: "",
          event: "武蔵国が和銅を献上され、元号が”和銅”になる",
        },
        {
          date: "709",
          person: "巨勢麻呂・佐伯石湯",
          event: "蝦夷を討つ",
        },
        {
          date: "710",
          person: "",
          event: "平城京に遷都",
        },
        {
          date: "712",
          person: "",
          event: "『古事記』が成立",
        },
        {
          date: "713",
          person: "",
          event: "寺が田野を占有しているのを取り戻す",
        },
        {
          date: "713",
          person: "",
          event: "乳牛の飼育開始",
        },
        {
          date: "713",
          person: "",
          event: "『風土記』撰上の詔",
        },
        {
          date: "718",
          person: "",
          event: "養老律が成立",
        },
        {
          date: "719",
          person: "",
          event: "初めて按察使を置く",
        },
        {
          date: "719",
          person: "",
          event: "衣服令で百章に右襟を命じる",
        },
        {
          date: "720",
          person: "",
          event: "『日本書紀』が成立",
        },
        {
          date: "720",
          person: "",
          event: "大伴旅人が隼人を討つ",
        },
        {
          date: "723",
          person: "",
          event: "三世一身法を定める",
        },
        {
          date: "724",
          person: "藤原宇合",
          event: "蝦夷を討つ。蝦夷との境界に多賀城を築く。",
        },
        {
          date: "733",
          person: "",
          event: "『出雲風土記』が完成",
        },
        {
          date: "734",
          person: "",
          event: "相撲節会の初め",
        },
        {
          date: "740",
          person: "",
          event: "藤原広嗣の乱",
        },
        {
          date: "741",
          person: "",
          event: "山背恭仁京に遷都",
        },
        {
          date: "741",
          person: "",
          event: "牛馬を殺すのを禁止する",
        },
        {
          date: "742",
          person: "",
          event: "大宰府の廃止",
        },
        {
          date: "743",
          person: "",
          event: "墾田永私財法を定める",
        },
        {
          date: "744",
          person: "",
          event: "難波京に遷都",
        },
        {
          date: "745",
          person: "",
          event: "大宰府の復活",
        },
        {
          date: "748",
          person: "",
          event: "諸国の田税を免ずる",
        },
        {
          date: "756",
          person: "聖武法皇",
          event: "崩御",
        },
        {
          date: "757",
          person: "",
          event: "諸臣に田地を与える",
        },
        {
          date: "758",
          person: "",
          event: "勤倹・礼節の美俗を令す",
        },
        {
          date: "759",
          person: "",
          event: "『万葉集』が成立",
        },
        {
          date: "765",
          person: "",
          event: "一切の墾田の私有を禁止する（寺院をのぞく）",
        },
        {
          date: "765",
          person: "道鏡",
          event: "太政大臣禅師になる",
        },
        {
          date: "766",
          person: "道鏡",
          event: "法王になる",
        },
        {
          date: "772",
          person: "",
          event: "再び墾田の私有を許可",
        },
        {
          date: "776",
          person: "",
          event: "検税使を諸国に派遣する",
        },
        {
          date: "780",
          person: "",
          event: "百姓から徴兵し武を習わせる",
        },
        {
          date: "783",
          person: "",
          event: "諸寺の田地買収の禁",
        },
        {
          date: "784",
          person: "",
          event: "山背長岡京に遷都",
        },
        {
          date: "785",
          person: "",
          event: "国司の正税私有の禁",
        },
        {
          date: "792",
          person: "",
          event: "学徒に漢音を習熟させる",
        },
        {
          date: "794",
          person: "",
          event: "平安京に遷都",
        },
        {
          date: "796",
          person: "",
          event: "隆平永宝という銭貨が造られる",
        },
        {
          date: "796",
          person: "",
          event: "東海道を開く",
        },
        {
          date: "797",
          person: "坂上田村麻呂",
          event: "鎮守将軍になる",
        },
        {
          date: "797",
          person: "",
          event: "『続日本紀』が完成",
        },
        {
          date: "799",
          person: "",
          event: "私稲を貸し出し利子を取ることを許す",
        },
        {
          date: "800",
          person: "",
          event: "官職を売るのを禁止する",
        },
        {
          date: "800",
          person: "",
          event: "富士山噴火",
        },
        {
          date: "801",
          person: "坂上田村麻呂",
          event: "蝦夷を平定",
        },
        {
          date: "805",
          person: "最澄",
          event: "天台宗を開く",
        },
        {
          date: "806",
          person: "空海",
          event: "真言宗を開く",
        },
        {
          date: "806",
          person: "",
          event: "王臣寺家の山野占有の禁",
        },
        {
          date: "807",
          person: "",
          event: "十五条の憲法を下す",
        },
        {
          date: "807",
          person: "",
          event: "畿内国司に私佃を許す",
        },
        {
          date: "807",
          person: "",
          event: "『古語拾遺』編纂完了",
        },
        {
          date: "808",
          person: "",
          event: "麦苗を刈るのを禁止",
        },
        {
          date: "810",
          person: "",
          event: "藤原薬子の乱",
        },
        {
          date: "811",
          person: "",
          event: "奥羽の開墾を奨励する",
        },
        {
          date: "813",
          person: "",
          event: "新羅人が肥前に侵寇",
        },
        {
          date: "815",
          person: "",
          event: "近畿地方に茶を植える",
        },
        {
          date: "816",
          person: "",
          event: "検非違使を置く",
        },
        {
          date: "818",
          person: "",
          event: "富寿神宝という銭貨を発行",
        },
        {
          date: "828",
          person: "",
          event: "畿内班田を行う",
        },
        {
          date: "829",
          person: "",
          event: "諸国に水車を造らせる",
        },
        {
          date: "833",
          person: "",
          event: "令義解の撰上",
        },
        {
          date: "833",
          person: "",
          event: "山城に魚の濫獲を禁止する",
        },
        {
          date: "835",
          person: "",
          event: "承和昌宝という銭貨を造る",
        },
        {
          date: "839",
          person: "",
          event: "東寺講堂諸像開眼供養",
        },
        {
          date: "842",
          person: "",
          event: "承和の変",
        },
        {
          date: "848",
          person: "",
          event: "長新宝という銭貨を造る",
        },
        {
          date: "850",
          person: "",
          event: "富者が山野江河地沼を占有するのを禁止",
        },
        {
          date: "854",
          person: "",
          event: "陸奥凶作により騒乱",
        },
        {
          date: "857",
          person: "",
          event: "大衍暦を廃止し五紀暦を用いる",
        },
        {
          date: "858",
          person: "藤原良房",
          event: "摂政になる",
        },
        {
          date: "859",
          person: "",
          event: "饒益神宝という銭貨を造る",
        },
        {
          date: "861",
          person: "",
          event: "宣明暦を行う",
        },
        {
          date: "864",
          person: "",
          event: "富士山噴火",
        },
        {
          date: "866",
          person: "",
          event: "応天門の変",
        },
        {
          date: "867",
          person: "",
          event: "京都に常平所をおく",
        },
        {
          date: "869",
          person: "",
          event: "陸奥大地震大津波",
        },
        {
          date: "869",
          person: "",
          event: "『続日本後紀』完成",
        },
        {
          date: "870",
          person: "",
          event: "貞観永宝という銭貨を造る",
        },
        {
          date: "871",
          person: "",
          event: "鳥海山が噴火",
        },
        {
          date: "874",
          person: "",
          event: "国司と郡司が百章の子女との婚姻を禁止する",
        },
        {
          date: "878",
          person: "",
          event: "京都飢饉",
        },
        {
          date: "878",
          person: "",
          event: "関東地方大地震",
        },
        {
          date: "881",
          person: "",
          event: "瀬戸内の海賊を追討",
        },
        {
          date: "883",
          person: "",
          event: "上総俘囚の乱",
        },
        {
          date: "887",
          person: "藤原基経",
          event: "関白になる",
        },
        {
          date: "887",
          person: "",
          event: "畿内大地震",
        },
        {
          date: "890",
          person: "",
          event: "寛平大宝という銭貨を造る",
        },
        {
          date: "894",
          person: "",
          event: "遣唐使を廃止",
        },
        {
          date: "895",
          person: "",
          event: "王臣諸家の私物出挙を禁止する",
        },
        {
          date: "896",
          person: "",
          event: "百姓の荒田閑地占有を禁止する",
        },
        {
          date: "899",
          person: "",
          event: "藤原時平左大臣・菅原道真右大臣を任官",
        },
        {
          date: "900",
          person: "",
          event: "三善清行が明の辛酉革命の議を奏す",
        },
        {
          date: "901",
          person: "菅原道真",
          event: "大宰権帥に左遷される",
        },
        {
          date: "901",
          person: "",
          event: "京都に味噌醸造が起こる",
        },
        {
          date: "902",
          person: "",
          event: "初めて荘園整理の令を下す",
        },
        {
          date: "905",
          person: "",
          event: "『古今和歌集』が成立",
        },
        {
          date: "907",
          person: "",
          event: "延喜通宝という銭貨を造る",
        },
        {
          date: "914",
          person: "",
          event: "美服を禁止する",
        },
        {
          date: "915",
          person: "",
          event: "疱瘡が流行する",
        },
        {
          date: "918",
          person: "",
          event: "深紅の服を禁止",
        },
        {
          date: "925",
          person: "",
          event: "風土記勘進の詔",
        },
        {
          date: "930",
          person: "藤原忠平",
          event: "摂政になる",
        },
        {
          date: "930",
          person: "",
          event: "疫病流行",
        },
        {
          date: "935",
          person: "平将門",
          event: "伯父の平国香を殺す",
        },
        {
          date: "935",
          person: "",
          event: "承平・天慶の乱がはじまる（～941）",
        },
        {
          date: "935",
          person: "",
          event: "呉越、初めて入貢",
        },
        {
          date: "935",
          person: "",
          event: "『土佐日記』",
        },
        {
          date: "937",
          person: "",
          event: "富士山噴火",
        },
        {
          date: "938",
          person: "空也",
          event: "念仏宗を創設",
        },
        {
          date: "940",
          person: "平貞盛・藤原秀郷ら",
          event: "平将門を誅す",
        },
        {
          date: "940",
          person: "藤原仲平",
          event: "書を呉越王に贈る",
        },
        {
          date: "947",
          person: "藤原実頼",
          event: "呉越王に書を贈る",
        },
        {
          date: "947",
          person: "",
          event: "疱瘡が流行し天皇と上皇も病気にかかる",
        },
        {
          date: "947",
          person: "菅原道真",
          event: "祠を北野に建てる",
        },
        {
          date: "951",
          person: "",
          event: "初めて和歌所を置く",
        },
        {
          date: "953",
          person: "藤原師輔",
          event: "呉越王に書を贈る",
        },
        {
          date: "986",
          person: "",
          event: "売買の法を定める",
        },
        {
          date: "987",
          person: "",
          event: "新制五箇条を定める",
        },
        {
          date: "988",
          person: "",
          event: "尾張の郡司や百姓が、国守藤原元命の非政を訴える",
        },
        {
          date: "1017",
          person: "藤原道長",
          event: "太政大臣になる",
        },
        {
          date: "1019",
          person: "",
          event: "刀伊の賊が入寇",
        },
        {
          date: "1028",
          person: "",
          event: "平忠常の乱が起こる",
        },
        {
          date: "1032",
          person: "",
          event: "富士山噴火",
        },
        {
          date: "1045",
          person: "",
          event: "寛徳の荘園停止令",
        },
        {
          date: "1083",
          person: "",
          event: "後三の役",
        },
        {
          date: "1083",
          person: "",
          event: "富士山噴火",
        },
        {
          date: "1086",
          person: "白河上皇",
          event: "院政開始",
        },
        {
          date: "1187",
          person: "源頼朝",
          event: "放生会を鶴岡八幡宮で行い、流鏑馬を見る",
        },
        {
          date: "1106",
          person: "",
          event: "京都で田楽が流行する",
        },
        {
          date: "1125",
          person: "",
          event: "京都大火",
        },
        {
          date: "1135",
          person: "鳥羽上皇",
          event: "穀を出して貧民を救う",
        },
        {
          date: "1145",
          person: "",
          event: "新制十四条を議定",
        },
        {
          date: "1156",
          person: "",
          event: "保元の乱",
        },
        {
          date: "1157",
          person: "",
          event: "新制三十五条を宣下",
        },
        {
          date: "1159",
          person: "",
          event: "平治の乱",
        },
        {
          date: "1167",
          person: "平清盛",
          event: "太政大臣になる",
        },
        {
          date: "1175",
          person: "法然",
          event: "浄土宗を開く",
        },
        {
          date: "1177",
          person: "",
          event: "鹿谷の蜜議",
        },
        {
          date: "1178",
          person: "",
          event: "新制十七条",
        },
        {
          date: "1179",
          person: "",
          event: "新制三十二条",
        },
        {
          date: "1180",
          person: "",
          event: "以仁王の令旨",
        },
        {
          date: "1180",
          person: "源頼政",
          event: "挙兵し、宇治平等院の戦いで自害",
        },
        {
          date: "1184",
          person: "",
          event: "一の谷の戦い",
        },
        {
          date: "1184",
          person: "",
          event: "公文所・間注所を設置",
        },
        {
          date: "1187",
          person: "",
          event: "『千載和歌集』",
        },
        {
          date: "1191",
          person: "栄西",
          event: "禅宗を日本に持ち帰る（臨済宗）",
        },
        {
          date: "1192",
          person: "源頼朝",
          event: "鎌倉幕府を開く",
        },
        {
          date: "1196",
          person: "近衞基通",
          event: "関白になる",
        },
        {
          date: "1200",
          person: "",
          event: "梶原景時・景季の変",
        },
        {
          date: "1201",
          person: "",
          event: "城長茂の乱",
        },
        {
          date: "1203",
          person: "",
          event: "比企能員の変",
        },
        {
          date: "1205",
          person: "北条時政",
          event: "源実朝の暗殺に失敗し出家する",
        },
        {
          date: "1205",
          person: "",
          event: "『新古今和歌集』",
        },
        {
          date: "1212",
          person: "",
          event: "新制二十一条ができる",
        },
        {
          date: "1212",
          person: "",
          event: "『方丈記』",
        },
        {
          date: "1219",
          person: "",
          event: "源氏が滅びる、北条氏の執権開始",
        },
        {
          date: "1221",
          person: "",
          event: "承久の乱",
        },
        {
          date: "1224",
          person: "親鸞",
          event: "「教行信証」を著す",
        },
        {
          date: "1232",
          person: "",
          event: "御成敗式目制定",
        },
        {
          date: "1235",
          person: "",
          event: "僧徒の武装を禁止する",
        },
        {
          date: "1235",
          person: "",
          event: "『小倉百人一首』の成立",
        },
        {
          date: "1236",
          person: "",
          event:
            "興福寺僧徒が暴動を起こしたため幕府は寺の荘園を没収し、大和に守護を置く",
        },
        {
          date: "1244",
          person: "",
          event: "幕府が奴婢養子・飢饉救助・人身売買・諸国守護奉行の法を定める",
        },
        {
          date: "1249",
          person: "",
          event: "引付衆を置く",
        },
        {
          date: "1253",
          person: "",
          event: "新制十八条",
        },
        {
          date: "1253",
          person: "日蓮",
          event: "法華宗を開く",
        },
        {
          date: "1253",
          person: "",
          event: "奴婢仕役法を定める",
        },
        {
          date: "1256",
          person: "",
          event: "北条時頼が最明寺に出家し、多くの武士も出家する",
        },
        {
          date: "1261",
          person: "",
          event: "徳政・新制二十一条を下す",
        },
        {
          date: "1266",
          person: "",
          event: "引付衆を廃止し、評定衆に聴訴せしむ",
        },
        {
          date: "1268",
          person: "日蓮",
          event: "外寇を警告する",
        },
        {
          date: "1269",
          person: "",
          event: "問注所を停止して五方引付衆を置く",
        },
        {
          date: "1274",
          person: "",
          event: "文永の役",
        },
        {
          date: "1275",
          person: "北条実政",
          event: "九州探題になる",
        },
        {
          date: "1276",
          person: "",
          event: "筑前の海岸に石塁を築く",
        },
        {
          date: "1281",
          person: "",
          event: "弘安の役",
        },
        {
          date: "1293",
          person: "",
          event: "一乗院の僧徒が大乗院の僧徒と合戦",
        },
        {
          date: "1293",
          person: "",
          event: "鎮西探題を置き北条兼時を任命する",
        },
        {
          date: "1297",
          person: "",
          event: "永人の徳政令",
        },
        {
          date: "1317",
          person: "",
          event: "文保の和談",
        },
        {
          date: "1320",
          person: "",
          event: "出羽の蝦夷が反乱",
        },
        {
          date: "1321",
          person: "",
          event: "院政が廃止され天皇親政となる",
        },
        {
          date: "1322",
          person: "",
          event: "東北の安東季久の乱",
        },
        {
          date: "1324",
          person: "",
          event: "正中の変",
        },
        {
          date: "1331",
          person: "",
          event: "元弘の乱",
        },
        {
          date: "1332",
          person: "後醍醐天皇",
          event: "隠岐に流される",
        },
        {
          date: "1333",
          person: "",
          event: "鎌倉幕府が滅びる",
        },
        {
          date: "1333",
          person: "",
          event: "記録所・雑訴決断所・武者所を置く",
        },
        {
          date: "1334",
          person: "",
          event: "建武の新政",
        },
        {
          date: "1335",
          person: "",
          event: "北条時行の乱",
        },
        {
          date: "1336",
          person: "",
          event: "湊川の戦い",
        },
        {
          date: "1338",
          person: "足利尊氏",
          event: "室町幕府を開く",
        },
        {
          date: "1349",
          person: "足利尊氏",
          event: "鎌倉公方になる",
        },
        {
          date: "1354",
          person: "",
          event: "近江土一揆",
        },
        {
          date: "1359",
          person: "",
          event: "筑後川の戦い",
        },
        {
          date: "1391",
          person: "",
          event: "明徳の乱",
        },
        {
          date: "1392",
          person: "",
          event: "南北朝が統一",
        },
        {
          date: "1399",
          person: "",
          event: "応永の乱",
        },
        {
          date: "1402",
          person: "足利義満",
          event: "明の国書を受く（義満が日本国王と呼ばれる）",
        },
        {
          date: "1404",
          person: "",
          event: "勘合貿易が始まる",
        },
        {
          date: "1426",
          person: "",
          event: "近江坂本の馬借一揆",
        },
        {
          date: "1428",
          person: "",
          event: "山城土一揆",
        },
        {
          date: "1439",
          person: "",
          event: "永享の乱",
        },
        {
          date: "1441",
          person: "",
          event: "嘉吉の変",
        },
        {
          date: "1447",
          person: "",
          event: "山城土一揆の民が徳政一揆",
        },
        {
          date: "1454",
          person: "",
          event: "享徳の大一揆",
        },
        {
          date: "1457",
          person: "大田道灌",
          event: "江戸城を築く",
        },
        {
          date: "1467",
          person: "",
          event: "応仁の乱が起きる",
        },
        {
          date: "1474",
          person: "足利義政",
          event: "朝鮮に書を送り、明の勘合符を求め、これを取得",
        },
        {
          date: "1477",
          person: "",
          event: "応仁の乱がようやく終わり、諸将の多くが国に帰る",
        },
        {
          date: "1478",
          person: "",
          event: "大内政弘が豊前・筑前を侵しこれを領有",
        },
        {
          date: "1482",
          person: "畠山義就",
          event: "室町幕府に抗す",
        },
        {
          date: "1482",
          person: "足利義政",
          event: "慈照寺を造営開始",
        },
        {
          date: "1485",
          person: "",
          event: "山城国一揆が起きる",
        },
        {
          date: "1488",
          person: "",
          event: "加賀一向一揆が起きる",
        },
        {
          date: "1489",
          person: "足利義政",
          event: "銀閣寺を完成させる",
        },
        {
          date: "1491",
          person: "北条早雲",
          event: "伊豆を占拠",
        },
        {
          date: "1501",
          person: "",
          event: "朝廷が即位礼の資金を幕府に求める",
        },
        {
          date: "1526",
          person: "今川氏親",
          event: "家法33条を定める",
        },
        {
          date: "1531",
          person: "",
          event: "一向一揆が起きる",
        },
        {
          date: "1536",
          person: "",
          event: "伊達稙宗が家法の塵芥集を定める",
        },
        {
          date: "1543",
          person: "",
          event: "種子島に鉄砲が伝わる",
        },
        {
          date: "1547",
          person: "武田信玄",
          event: "民制55条を定める",
        },
        {
          date: "1549",
          person: "ザビエル",
          event: "キリスト教を伝える",
        },
        {
          date: "1555",
          person: "",
          event: "川中島の戦い",
        },
        {
          date: "1571",
          person: "",
          event: "織田信長が米を京都の民に貸し、その利をもって供御に充つ",
        },
        {
          date: "1560",
          person: "",
          event: "桶狭間の戦い",
        },
        {
          date: "1568",
          person: "織田信長",
          event: "入京",
        },
        {
          date: "1571",
          person: "織田信長",
          event: "比叡山を焼き打ち",
        },
        {
          date: "1573",
          person: "",
          event: "室町幕府が滅ぶ",
        },
        {
          date: "1575",
          person: "",
          event: "長篠の戦い",
        },
        {
          date: "1577",
          person: "織田信長",
          event: "織田信長が安土を楽市にする",
        },
        {
          date: "1582",
          person: "明智光秀",
          event: "本能寺の変",
        },
        {
          date: "1582",
          person: "",
          event: "太閤検地（～1598）",
        },
        {
          date: "1585",
          person: "豊臣秀吉",
          event: "関白になる",
        },
        {
          date: "1588",
          person: "豊臣秀吉",
          event: "刀狩令を発する",
        },
        {
          date: "1590",
          person: "豊臣秀吉",
          event: "全国統一",
        },
        {
          date: "1591",
          person: "豊臣秀吉",
          event: "戸口調査を実施",
        },
        {
          date: "1592",
          person: "",
          event: "文禄の役",
        },
        {
          date: "1592",
          person: "豊臣秀吉",
          event: "朱印船制度を定める",
        },
        {
          date: "1597",
          person: "",
          event: "慶長の役",
        },
        {
          date: "1600",
          person: "",
          event: "関ヶ原の戦い",
        },
        {
          date: "1603",
          person: "徳川家康",
          event: "江戸幕府を開く",
        },
        {
          date: "1604",
          person: "",
          event: "江戸幕府が正式に朱印船貿易をはじめる",
        },
        {
          date: "1605",
          person: "",
          event: "煙草が流行する",
        },
        {
          date: "1609",
          person: "",
          event: "煙草を禁止する",
        },
        {
          date: "1610",
          person: "",
          event: "足尾銅山を発見",
        },
        {
          date: "1612",
          person: "",
          event: "岡本大八を処刑（禁教の発端となる）",
        },
        {
          date: "1614",
          person: "",
          event: "大阪冬の陣",
        },
        {
          date: "1614",
          person: "",
          event: "朝鮮活字で大蔵経を印刷",
        },
        {
          date: "1615",
          person: "",
          event: "武家諸法度・禁中並公家諸法度が公布される",
        },
        {
          date: "1616",
          person: "",
          event: "欧船の来航を長崎の平戸に制限する",
        },
        {
          date: "1616",
          person: "",
          event: "煙草の栽培を禁止",
        },
        {
          date: "1616",
          person: "",
          event: "人身売買を禁止する",
        },
        {
          date: "1617",
          person: "",
          event: "江戸吉原遊郭の開設を許す",
        },
        {
          date: "1623",
          person: "",
          event: "イギリスの平戸での貿易を停止",
        },
        {
          date: "1624",
          person: "",
          event: "イスパニア人の来航を禁止",
        },
        {
          date: "1628",
          person: "",
          event: "百姓の衣類に絹類を使用することを禁止",
        },
        {
          date: "1630",
          person: "",
          event: "キリスト教関係の書物の輸入を禁止",
        },
        {
          date: "1633",
          person: "",
          event: "奉書船以外の海外渡航を禁止し、海外渡航者の帰国を制限する",
        },
        {
          date: "1635",
          person: "",
          event: "参勤交代制の確立",
        },
        {
          date: "1635",
          person: "",
          event:
            "すべての日本船の渡航を禁止し、帰国者は死刑とする。唐船も長崎に限定する。",
        },
        {
          date: "1637",
          person: "",
          event: "島原の乱",
        },
        {
          date: "1639",
          person: "",
          event: "ポルトガル人の来航を禁止する",
        },
        {
          date: "1641",
          person: "",
          event: "オランダ人を長崎の出島に移す→鎖国の完成",
        },
        {
          date: "1643",
          person: "",
          event: "田畑永代売買の禁",
        },
        {
          date: "1649",
          person: "",
          event: "慶安の御触書",
        },
        {
          date: "1649",
          person: "",
          event: "大名・旗本に倹約令",
        },
        {
          date: "1651",
          person: "",
          event: "由比正雪の乱",
        },
        {
          date: "1655",
          person: "",
          event: "オランダ人の糸割符制を廃止し、相対貿易とする",
        },
        {
          date: "1657",
          person: "",
          event: "江戸明歴の大火により江戸城本丸が焼失する",
        },
        {
          date: "1657",
          person: "",
          event: "株仲間の独占を禁止する",
        },
        {
          date: "1657",
          person: "",
          event: "水戸藩主の徳川光圀が『大日本史』の編集を始める",
        },
        {
          date: "1663",
          person: "",
          event: "殉死を禁止する",
        },
        {
          date: "1665",
          person: "",
          event: "大名の人質を廃止する",
        },
        {
          date: "1668",
          person: "",
          event: "倹約令",
        },
        {
          date: "1673",
          person: "",
          event: "分地制限令",
        },
        {
          date: "1673",
          person: "市川団十郎",
          event: "江戸に歌舞伎を開く",
        },
        {
          date: "1675",
          person: "",
          event: "関東諸国に鉄砲私蔵を禁ず",
        },
        {
          date: "1678",
          person: "坂田藤十郎",
          event: "大阪に歌舞伎を確立",
        },
        {
          date: "1682",
          person: "井原西鶴",
          event: "『好色一代男』が刊行",
        },
        {
          date: "1684",
          person: "安井算哲",
          event: "貞享暦を作る",
        },
        {
          date: "1687",
          person: "",
          event: "徳川綱吉により生類憐みの令が出される",
        },
        {
          date: "1688",
          person: "",
          event: "元禄時代開始",
        },
        {
          date: "1693",
          person: "",
          event: "朝鮮との竹島問題が起きる",
        },
        {
          date: "1695",
          person: "",
          event: "貨幣改鋳の出目を以て幕府財政の急を救う",
        },
        {
          date: "1697",
          person: "",
          event: "農業全書を刊行",
        },
        {
          date: "1702",
          person: "",
          event: "赤穂浪士の討ち入り",
        },
        {
          date: "1702",
          person: "松尾芭蕉",
          event: "『奥の細道』が刊行される",
        },
        {
          date: "1708",
          person: "",
          event: "宝永通宝を新鋳",
        },
        {
          date: "1708",
          person: "シドッチ",
          event: "イタリアの宣教師、来日",
        },
        {
          date: "1709",
          person: "",
          event: "新井白石を登用",
        },
        {
          date: "1709",
          person: "",
          event: "生類憐みの令を廃止",
        },
        {
          date: "1715",
          person: "",
          event: "金銀の海外流出を防ぐため、長崎貿易制限新令を発する",
        },
        {
          date: "1716",
          person: "",
          event: "享保の改革",
        },
        {
          date: "1717",
          person: "大岡忠相",
          event: "江戸町奉行に就任",
        },
        {
          date: "1720",
          person: "",
          event: "洋書輸入の禁を緩和する",
        },
        {
          date: "1720",
          person: "",
          event: "江戸町火消いろは組を創設する",
        },
        {
          date: "1721",
          person: "",
          event: "目安箱の設置",
        },
        {
          date: "1722",
          person: "",
          event: "上米の制を設けて、参勤交代を緩める。新田開発を奨励する。",
        },
        {
          date: "1724",
          person: "",
          event: "倹約令を廃止し、衣服の売価を制限する",
        },
        {
          date: "1726",
          person: "",
          event: "物価取締令",
        },
        {
          date: "1742",
          person: "",
          event: "公事方御定書",
        },
        {
          date: "1744",
          person: "",
          event: "倹約令",
        },
        {
          date: "1756",
          person: "",
          event: "米の価格が高騰したため蓄米を禁止する",
        },
        {
          date: "1758",
          person: "",
          event: "宝暦事件",
        },
        {
          date: "1764",
          person: "",
          event: "倹約令をやめ、財政再建を計る",
        },
        {
          date: "1764",
          person: "",
          event: "江戸の町人に新田開発を奨励する",
        },
        {
          date: "1765",
          person: "",
          event: "関東の農民20万人による大一揆が起きる",
        },
        {
          date: "1767",
          person: "",
          event: "明和事件",
        },
        {
          date: "1772",
          person: "田村意次",
          event: "老中になる",
        },
        {
          date: "1774",
          person: "杉田玄白",
          event: "『解体新書』を刊行",
        },
        {
          date: "1777",
          person: "",
          event: "百姓の江戸出稼ぎを禁止。新田の開発を命じる。",
        },
        {
          date: "1778",
          person: "",
          event: "ロシア船が蝦夷地に来航し通商を求めるが、松前氏が拒否",
        },
        {
          date: "1783",
          person: "",
          event: "天明の大飢饉",
        },
        {
          date: "1784",
          person: "",
          event: "蝦夷地の開拓を始める",
        },
        {
          date: "1787",
          person: "松平定信",
          event: "老中になり寛政の改革を行う",
        },
        {
          date: "1787",
          person: "",
          event: "米の価格が暴騰し、天命の打ちこわしが起きる",
        },
        {
          date: "1789",
          person: "",
          event: "棄損令を発して、旗本の御家人の負債を免除する",
        },
        {
          date: "1790",
          person: "",
          event: "寛政異学の禁",
        },
        {
          date: "1790",
          person: "",
          event: "江戸の銭湯に男女の混浴を禁止する",
        },
        {
          date: "1792",
          person: "ロシア使節のラクスマン",
          event:
            "が漂民の幸太夫を伴い根室に来て、通商の要求をする。幕府はこれを拒否",
        },
        {
          date: "1797",
          person: "",
          event: "イギリス船が蝦夷地に来航",
        },
        {
          date: "1798",
          person: "本居宣長",
          event: "『古事記伝』を完成させる",
        },
        {
          date: "1800",
          person: "伊能忠敬",
          event: "蝦夷地を測量",
        },
        {
          date: "1804",
          person: "ロシア使節のレザノフ",
          event: "長崎に来航",
        },
        {
          date: "1806",
          person: "",
          event: "江戸の町人に御用金を命ずる",
        },
        {
          date: "1808",
          person: "",
          event: "イギリス船フェートン号が長崎に来航",
        },
        {
          date: "1812",
          person: "高田屋嘉兵衛",
          event: "ロシア艦に捕えらる",
        },
        {
          date: "1813",
          person: "",
          event: "イギリス船来航",
        },
        {
          date: "1815",
          person: "",
          event: "座頭の高利貸を禁止",
        },
        {
          date: "1816",
          person: "",
          event: "イギリス船が琉球に来て通商を要求",
        },
        {
          date: "1817",
          person: "",
          event: "イギリス船が浦賀に来航",
        },
        {
          date: "1821",
          person: "伊能忠敬の",
          event: "大日本沿海興地図が完成",
        },
        {
          date: "1824",
          person: "",
          event: "イギリス捕鯨船員が常陸・薩摩に上陸",
        },
        {
          date: "1825",
          person: "",
          event: "外国船打払令",
        },
        {
          date: "1827",
          person: "頼山陽",
          event: "『日本外史』",
        },
        {
          date: "1828",
          person: "",
          event: "シーボルト事件",
        },
        {
          date: "1834",
          person: "水野忠邦",
          event: "老中になる",
        },
        {
          date: "1835",
          person: "",
          event: "天保通宝を新鋳",
        },
        {
          date: "1837",
          person: "",
          event: "大塩平八郎の乱",
        },
        {
          date: "1837",
          person: "",
          event:
            "アメリカ船のモリソン号が漂民を伴って浦賀に入港するが、打ち払い令により撃退",
        },
        {
          date: "1839",
          person: "",
          event: "蛮社の獄",
        },
        {
          date: "1840",
          person: "",
          event: "清の商人がアヘン戦争を報じ来る",
        },
        {
          date: "1841",
          person: "",
          event: "天保の改革",
        },
        {
          date: "1841",
          person: "",
          event: "全国の株仲間を禁止",
        },
        {
          date: "1842",
          person: "",
          event: "天保暦を採用",
        },
        {
          date: "1844",
          person: "",
          event: "フランス船が琉球に来航",
        },
        {
          date: "1847",
          person: "島津氏",
          event: "琉球をイギリス・フランスに開港",
        },
        {
          date: "1848",
          person: "",
          event: "株仲間の再興を許可",
        },
        {
          date: "1848",
          person: "",
          event: "佐久間象山が大砲を鋳造",
        },
        {
          date: "1849",
          person: "",
          event: "イギリス船が浦賀に来航",
        },
        {
          date: "1852",
          person: "",
          event: "ロシア船が下田に来航",
        },
        {
          date: "1853",
          person: "アメリカ使節のペリー",
          event: "浦賀に来航。幕府が開国の可否を諸侯有司に問う",
        },
        {
          date: "1854",
          person: "",
          event: "日米和親条約調印",
        },
        {
          date: "1858",
          person: "",
          event: "日米修好通商条約調印",
        },
        {
          date: "1859",
          person: "",
          event: "安政の大獄",
        },
        {
          date: "1860",
          person: "",
          event: "桜田門外の変",
        },
        {
          date: "1860",
          person: "",
          event: "ヒュースケン殺害",
        },
        {
          date: "1862",
          person: "",
          event: "生麦事件",
        },
        {
          date: "1862",
          person: "",
          event: "坂下門外の変",
        },
        {
          date: "1863",
          person: "",
          event: "8月18日の政変、天誅組の変、生野銀山の変",
        },
        {
          date: "1863",
          person: "",
          event: "長州藩が外国船を砲撃",
        },
        {
          date: "1863",
          person: "",
          event: "薩英戦争",
        },
        {
          date: "1864",
          person: "",
          event: "四国艦隊下関砲撃",
        },
        {
          date: "1864",
          person: "",
          event: "長州征伐",
        },
        {
          date: "1865",
          person: "",
          event: "横浜製鉄所・横須賀造船所起工",
        },
        {
          date: "1866",
          person: "",
          event: "江戸・大阪で打ちこわし",
        },
        {
          date: "1867",
          person: "",
          event: "ええじゃないか運動",
        },
        {
          date: "1867",
          person: "",
          event: "貿易額輸入超過となる",
        },
        {
          date: "1867",
          person: "",
          event: "大政奉還",
        },
        {
          date: "1867",
          person: "",
          event: "王政復古の大号令",
        },
        {
          date: "1868",
          person: "",
          event: "明治維新、五箇条の御誓文（鳥羽伏見の戦い、江戸城明け渡し）",
        },
        {
          date: "1868",
          person: "",
          event: "神仏分離令",
        },
        {
          date: "1869",
          person: "",
          event: "版籍奉還",
        },
        {
          date: "1870",
          person: "",
          event: "平民の苗字を許す",
        },
        {
          date: "1870",
          person: "",
          event: "人力車の発明",
        },
        {
          date: "1871",
          person: "",
          event: "廃藩置県",
        },
        {
          date: "1871",
          person: "",
          event: "岩倉具視らが欧米へ行く",
        },
        {
          date: "1871",
          person: "",
          event: "えた非人を廃止",
        },
        {
          date: "1872",
          person: "",
          event: "太陽暦を採用",
        },
        {
          date: "1872",
          person: "",
          event: "富岡製糸場が開業",
        },
        {
          date: "1872",
          person: "福沢諭吉",
          event: "『学問のすすめ』",
        },
        {
          date: "1873",
          person: "",
          event: "徴兵令、地租改正",
        },
        {
          date: "1873",
          person: "",
          event: "岩倉具視らが日本に戻り、西郷隆盛らの征韓論が敗れる",
        },
        {
          date: "1873",
          person: "",
          event: "ウィーン万国博覧会に参加",
        },
        {
          date: "1873",
          person: "",
          event: "東京上野公園が公開される",
        },
        {
          date: "1873",
          person: "",
          event: "仇討ちを禁止",
        },
        {
          date: "1875",
          person: "",
          event: "ロシアと千島・樺太の交換",
        },
        {
          date: "1875",
          person: "",
          event: "東京気象台を設置",
        },
        {
          date: "1876",
          person: "",
          event: "海軍兵学校を置く",
        },
        {
          date: "1876",
          person: "",
          event: "日曜を休日、土曜日を半休にする",
        },
        {
          date: "1877",
          person: "西郷隆盛",
          event: "西南戦争",
        },
        {
          date: "1878",
          person: "大久保利通",
          event: "暗殺される",
        },
        {
          date: "1878",
          person: "",
          event: "郡区町村制編成法・府県会規則・地方税規制を公布",
        },
        {
          date: "1878",
          person: "",
          event: "陸軍士官学校が創立。参謀本部設置。",
        },
        {
          date: "1879",
          person: "",
          event: "教育令を制定",
        },
        {
          date: "1880",
          person: "",
          event: "刑法・治罪法を公布",
        },
        {
          date: "1881",
          person: "",
          event: "国会開設の詔。自由党が成立",
        },
        {
          date: "1882",
          person: "",
          event: "立憲改進党が成立",
        },
        {
          date: "1882",
          person: "",
          event: "日本銀行設立",
        },
        {
          date: "1882",
          person: "",
          event: "最初の私鉄（日本鉄道会社）の設立が許可される",
        },
        {
          date: "1882",
          person: "",
          event: "壬午事変",
        },
        {
          date: "1884",
          person: "",
          event: "甲申事件",
        },
        {
          date: "1885",
          person: "",
          event: "内閣制度実施",
        },
        {
          date: "1885",
          person: "",
          event: "日本銀行が初めて兌換券を発行する",
        },
        {
          date: "1886",
          person: "",
          event: "第一回条約改正会議",
        },
        {
          date: "1886",
          person: "",
          event: "帝京大学（東京大学）創立。小学校令・中学校令を公布",
        },
        {
          date: "1888",
          person: "",
          event: "市制・町村制を公布",
        },
        {
          date: "1889",
          person: "",
          event: "大日本帝国憲法の発布。皇室典範の発布",
        },
        {
          date: "1889",
          person: "",
          event: "地租条例を改正",
        },
        {
          date: "1889",
          person: "",
          event: "東海道本線ができる",
        },
        {
          date: "1890",
          person: "",
          event: "第一回帝国議会",
        },
        {
          date: "1890",
          person: "",
          event: "北里柴三郎が破傷風血清治療法を発見",
        },
        {
          date: "1890",
          person: "",
          event: "教育勅語発布",
        },
        {
          date: "1890",
          person: "",
          event: "民法・刑事訴訟法・民事訴訟法・商法の公布",
        },
        {
          date: "1890",
          person: "",
          event: "第一回帝国議会を開く",
        },
        {
          date: "1892",
          person: "",
          event: "条約改正委員会を設置",
        },
        {
          date: "1894",
          person: "",
          event: "日清戦争開始",
        },
        {
          date: "1895",
          person: "",
          event: "下関条約調印、三国干渉",
        },
        {
          date: "1897",
          person: "",
          event: "貨幣法の公布、金本位制の確立",
        },
        {
          date: "1897",
          person: "",
          event: "赤痢菌を発見（志賀潔）",
        },
        {
          date: "1899",
          person: "",
          event: "改訂新条約実施に関する詔書",
        },
        {
          date: "1900",
          person: "",
          event: "北清事変",
        },
        {
          date: "1900",
          person: "伊藤博文",
          event: "政友会を組織",
        },
        {
          date: "1901",
          person: "",
          event: "八幡製鉄所の創業",
        },
        {
          date: "1901",
          person: "",
          event: "日本赤十字社条例を公布",
        },
        {
          date: "1902",
          person: "",
          event: "日英同盟成立",
        },
        {
          date: "1903",
          person: "",
          event: "小学校国定教科書制度を公布",
        },
        {
          date: "1904",
          person: "",
          event: "日露戦争開始",
        },
        {
          date: "1905",
          person: "",
          event: "ポーツマス条約調印",
        },
        {
          date: "1905",
          person: "",
          event: "平民社メーデー茶話会。講和反対日比谷騒乱。",
        },
        {
          date: "1906",
          person: "",
          event: "南満州鉄道株式会社を創立",
        },
        {
          date: "1906",
          person: "",
          event: "鉄道国有法・京釜鉄道買収法・関税定率法の改正と公布",
        },
        {
          date: "1908",
          person: "",
          event: "戊申詔書",
        },
        {
          date: "1909",
          person: "伊藤博文",
          event: "狙撃されて亡くなる",
        },
        {
          date: "1910",
          person: "",
          event: "大逆事件、日韓併合",
        },
        {
          date: "1911",
          person: "",
          event: "野口英世が梅毒スピロヘータ純粋培養に成功",
        },
        {
          date: "1911",
          person: "",
          event: "日米・日英・日独修交通商航海条約（関税自主権の確立）",
        },
        {
          date: "1911",
          person: "",
          event: "東京・大阪に特別高等警察を設置",
        },
        {
          date: "1911",
          person: "西田幾多郎",
          event: "『善の研究』",
        },
        {
          date: "1912",
          person: "",
          event: "国際紛争平和的処理条約調印",
        },
        {
          date: "1912",
          person: "明治天皇",
          event: "崩御",
        },
        {
          date: "1913",
          person: "",
          event: "第一次護憲運動が起きる",
        },
        {
          date: "1913",
          person: "",
          event: "日比谷暴動",
        },
        {
          date: "1914",
          person: "",
          event:
            "第一次世界大戦開始（～1918）。ドイツに対し宣戦し世界大会に参加。株価大暴落。",
        },
        {
          date: "1915",
          person: "",
          event: "中国に対して21ヶ条の要求交渉",
        },
        {
          date: "1915",
          person: "芥川龍之介",
          event: "『羅生門』",
        },
        {
          date: "1917",
          person: "",
          event: "臨時教育会議を設置",
        },
        {
          date: "1917",
          person: "",
          event: "理化学研究所を設立",
        },
        {
          date: "1918",
          person: "",
          event: "シベリア出兵、米騒動",
        },
        {
          date: "1919",
          person: "",
          event: "朝鮮万歳事件",
        },
        {
          date: "1919",
          person: "",
          event: "普通選挙獲得運動が起きる",
        },
        {
          date: "1920",
          person: "",
          event: "経済恐慌",
        },
        {
          date: "1920",
          person: "",
          event: "国際連盟に加入し常任理事国になる",
        },
        {
          date: "1922",
          person: "",
          event: "ワシントン条約",
        },
        {
          date: "1923",
          person: "",
          event: "関東大震災",
        },
        {
          date: "1925",
          person: "",
          event: "治安維持法、普通選挙法",
        },
        {
          date: "1925",
          person: "",
          event: "全国労働組合協議会が結成される",
        },
        {
          date: "1925",
          person: "",
          event: "東京放送局がラジオ放送を開始",
        },
        {
          date: "1926",
          person: "",
          event: "日本放送協会が成立",
        },
        {
          date: "1926",
          person: "大正天皇",
          event: "崩御",
        },
        {
          date: "1928",
          person: "",
          event: "普通選挙法による最初の衆議院議員総選挙",
        },
        {
          date: "1929",
          person: "",
          event: "金融大恐慌",
        },
        {
          date: "1930",
          person: "",
          event: "ロンドン条約",
        },
        {
          date: "1931",
          person: "",
          event: "満州事変",
        },
        {
          date: "1931",
          person: "",
          event: "金の輸出を禁止",
        },
        {
          date: "1932",
          person: "",
          event: "五・一五事件、満州国建国",
        },
        {
          date: "1933",
          person: "",
          event: "国際連盟脱退",
        },
        {
          date: "1934",
          person: "",
          event: "満州国で帝制を実施",
        },
        {
          date: "1934",
          person: "",
          event: "右翼労働運動",
        },
        {
          date: "1936",
          person: "",
          event: "二・二六事件",
        },
        {
          date: "1936",
          person: "",
          event: "日独防共協定",
        },
        {
          date: "1936",
          person: "",
          event: "米穀自治管理法",
        },
        {
          date: "1937",
          person: "",
          event: "日中戦争、盧溝橋事件",
        },
        {
          date: "1937",
          person: "",
          event: "日独伊三国防共協定",
        },
        {
          date: "1938",
          person: "",
          event: "国家総動員法が成立。綿糸配給切符制。",
        },
        {
          date: "1939",
          person: "",
          event: "賃銀統制令・価格統制法",
        },
        {
          date: "1940",
          person: "",
          event: "日独伊三国軍事同盟",
        },
        {
          date: "1940",
          person: "",
          event: "小麦粉・米穀・砂糖配給統制",
        },
        {
          date: "1940",
          person: "",
          event: "大政翼賛会創立",
        },
        {
          date: "1941",
          person: "",
          event: "東条内閣成立",
        },
        {
          date: "1941",
          person: "",
          event: "太平洋戦争開始（～1945）",
        },
        {
          date: "1941",
          person: "",
          event: "言論出版等臨時取締令",
        },
        {
          date: "1942",
          person: "",
          event: "食料管理法",
        },
        {
          date: "1942",
          person: "",
          event: "新聞統制",
        },
        {
          date: "1943",
          person: "",
          event: "大東亜会議",
        },
        {
          date: "1944",
          person: "",
          event: "防空壕の強制施行、竹やり訓練実施",
        },
        {
          date: "1945",
          person: "",
          event: "広島と長崎に原爆が投下される",
        },
        {
          date: "1945",
          person: "",
          event: "ポツダム宣言受諾、財閥解体、農地改革、労働組合法",
        },
        {
          date: "1946",
          person: "",
          event: "天皇神格否定の詔書",
        },
        {
          date: "1946",
          person: "",
          event: "日本国憲法公布、東京裁判開始",
        },
        {
          date: "1947",
          person: "",
          event: "第一回特別国会",
        },
        {
          date: "1947",
          person: "",
          event: "六三三制新教育開始",
        },
        {
          date: "1947",
          person: "",
          event: "独占禁止法",
        },
        {
          date: "1948",
          person: "",
          event: "海上保安庁設置",
        },
        {
          date: "1949",
          person: "湯川秀樹",
          event: "ノーベル賞獲得",
        },
        {
          date: "1949",
          person: "",
          event: "単一為替レート決定（1ドル＝360円）",
        },
        {
          date: "1950",
          person: "",
          event: "朝鮮動乱による特需発生",
        },
        {
          date: "1950",
          person: "",
          event: "米三軍首脳が来日。日本の軍事基地化声明。",
        },
        {
          date: "1950",
          person: "",
          event: "朝鮮戦争、警察予備隊を設置",
        },
        {
          date: "1950",
          person: "",
          event: "レッドパージ（共産追放）",
        },
        {
          date: "1951",
          person: "",
          event: "サンフランシスコ平和条約、日米安全保障条約",
        },
        {
          date: "1951",
          person: "",
          event: "ユネスコに加入",
        },
        {
          date: "1952",
          person: "",
          event: "日米行政協定",
        },
        {
          date: "1954",
          person: "",
          event: "MSA協定、自衛隊発足",
        },
        {
          date: "1954",
          person: "",
          event: "福龍丸ビキニ水爆被災事件",
        },
        {
          date: "1954",
          person: "",
          event: "教員の政治活動制限",
        },
        {
          date: "1955",
          person: "",
          event: "ガット加入、原子力基本法",
        },
        {
          date: "1955",
          person: "",
          event: "ドムニツキー文書公表",
        },
        {
          date: "1956",
          person: "",
          event: "国際連合に加入",
        },
        {
          date: "1956",
          person: "",
          event: "神武景気",
        },
        {
          date: "1956",
          person: "",
          event: "原子力委員会発足",
        },
        {
          date: "1957",
          person: "",
          event: "日ソ通商条約調印",
        },
        {
          date: "1957",
          person: "",
          event: "なべ底景気",
        },
        {
          date: "1958",
          person: "",
          event: "全日本農民組合連合会の結成",
        },
        {
          date: "1958",
          person: "",
          event: "新特急こだま号の運転開始、東京タワー完成",
        },
        {
          date: "1959",
          person: "",
          event: "岩戸景気",
        },
        {
          date: "1960",
          person: "",
          event: "日米新安保条約調印",
        },
        {
          date: "1960",
          person: "",
          event: "日米安全保障条約の承認案を深夜に可決。安保騒動が起きる。",
        },
        {
          date: "1960",
          person: "",
          event: "六・一六事件",
        },
        {
          date: "1960",
          person: "",
          event: "カラーテレビ本放送開始",
        },
        {
          date: "1961",
          person: "",
          event: "農業基本法成立",
        },
        {
          date: "1961",
          person: "",
          event: "株価大暴落、金融引き締め",
        },
        {
          date: "1962",
          person: "",
          event: "日英通商航海条約調印",
        },
        {
          date: "1962",
          person: "",
          event: "日中総合貿易覚書調印",
        },
        {
          date: "1962",
          person: "",
          event: "都市にスモッグ発生",
        },
        {
          date: "1964",
          person: "",
          event: "林業基本法成立",
        },
        {
          date: "1964",
          person: "",
          event: "東京オリンピック",
        },
        {
          date: "1965",
          person: "",
          event: "日韓基本条約に調印",
        },
        {
          date: "1966",
          person: "",
          event: "基地基本法の成立",
        },
        {
          date: "1966",
          person: "",
          event: "日ソ貿易協定・日ソ航空協定に調印",
        },
        {
          date: "1966",
          person: "",
          event: "第1回赤字国債発行",
        },
        {
          date: "1967",
          person: "",
          event: "東京都知事選挙で革新系の美濃部亮吉が当選",
        },
        {
          date: "1967",
          person: "",
          event: "ケネディ=ラウンド調印",
        },
        {
          date: "1967",
          person: "",
          event: "資本自由化を正式に実施",
        },
        {
          date: "1968",
          person: "",
          event: "日米貿易経済合同委員会ホノルル会議",
        },
        {
          date: "1968",
          person: "",
          event: "第2次日中総合貿易協定に調印",
        },
        {
          date: "1968",
          person: "",
          event: "小笠原諸島復帰",
        },
        {
          date: "1968",
          person: "",
          event: "大学紛争拡大",
        },
        {
          date: "1969",
          person: "",
          event: "大学運営臨時措置法案が強行可決される",
        },
        {
          date: "1969",
          person: "",
          event: "軍縮委員会へ初参加",
        },
        {
          date: "1969",
          person: "",
          event: "いざなぎ景気",
        },
        {
          date: "1970",
          person: "",
          event: "核拡散防止条約に調印",
        },
        {
          date: "1970",
          person: "",
          event: "日米安全保障条約を延長",
        },
        {
          date: "1970",
          person: "",
          event: "日本万国博覧会",
        },
        {
          date: "1970",
          person: "",
          event: "国産人工衛星「おおすみ」の打ち上げに成功",
        },
        {
          date: "1971",
          person: "",
          event: "沖縄返還協定に調印",
        },
        {
          date: "1971",
          person: "",
          event: "ドル=ショック",
        },
        {
          date: "1972",
          person: "",
          event: "沖縄県が復活",
        },
        {
          date: "1972",
          person: "",
          event: "日中国交正常化",
        },
        {
          date: "1973",
          person: "",
          event: "中東戦争によるオイルショック、インフレ",
        },
        {
          date: "1973",
          person: "",
          event: "公害罪を設置",
        },
        {
          date: "1976",
          person: "",
          event: "ロッキード疑獄事件が広まる",
        },
        {
          date: "1976",
          person: "",
          event: "被占領下外交文書が公開される",
        },
        {
          date: "1977",
          person: "",
          event: "了解12海里法・漁業水域200海里暫定措置法の成立",
        },
        {
          date: "1978",
          person: "",
          event: "日中平和友好条約に調印",
        },
        {
          date: "1979",
          person: "",
          event: "東京サミット",
        },
        {
          date: "1979",
          person: "",
          event: "グラマン・ダグラス疑獄事件",
        },
        {
          date: "1980",
          person: "",
          event: "国連の婦人差別撤廃条約に署名",
        },
        {
          date: "1981",
          person: "",
          event: "行政改革推進本部が発足",
        },
        {
          date: "1982",
          person: "",
          event: "ＩＢＭ産業スパイ事件",
        },
        {
          date: "1982",
          person: "",
          event: "教科書記述について中国・韓国から抗議",
        },
        {
          date: "1985",
          person: "",
          event: "バブル経済発生",
        },
        {
          date: "1985",
          person: "",
          event: "男女雇用機会均等法",
        },
        {
          date: "1985",
          person: "",
          event: "科学万博つくば85",
        },
        {
          date: "1986",
          person: "",
          event: "東京サミット",
        },
        {
          date: "1987",
          person: "",
          event: "アメリカが対日経済制裁措置を発表",
        },
        {
          date: "1987",
          person: "",
          event: "世界七大宗教者会議",
        },
        {
          date: "1988",
          person: "",
          event: "日米の牛肉・オレンジ交渉に決着がつく",
        },
        {
          date: "1989",
          person: "昭和天皇",
          event: "崩御",
        },
      ],
    };
  },
  mounted() {
    this.years();
  },
  methods: {
    years() {
      for (var y = this.start; y < this.last; y += this.step) {
        this.year.push(y);
      }
    },
    period(y) {
      switch (true) {
        case y < -400:
          return "縄文";
          break;
        case y < 250:
          return "弥生";
          break;
        case y < 592:
          return "古墳";
          break;
        case y < 710:
          return "飛鳥";
          break;
        case y < 794:
          return "奈良";
          break;
        case y < 1185:
          return "平安";
          break;
        case y < 1136:
          return "鎌倉";
          break;
        case y < 1467:
          return "室町";
          break;
        case y < 1603:
          return "戦国";
          break;
        case y < 1868:
          return "江戸";
          break;
        case y < 1912:
          return "明治";
          break;
        case y < 1926:
          return "大正";
          break;
        case y < 1989:
          return "昭和";
          break;
        case y < 2019:
          return "平成";
          break;
        default:
          return "令和";
          break;
      }
    },
  },
  computed: {
    // yea() {
    //   console.log("te");
    //   return this.last;
    // },
  },
});
</script>

<style>
.chronology th,
.chronology td {
  padding: 0 0.5rem;
}
</style>
