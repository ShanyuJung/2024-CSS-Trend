<template>
  <div class="timeline-scroll-container">
    <div class="progress"></div>
    <div class="container">
      <h1>Apple Inc.</h1>
      <img
        src="https://www.apple.com/newsroom/images/live-action/new-store-opening/Apple-Store-fifth-avenue-new-york-redesign-exterior-091919_big.jpg.large.jpg"
        alt=""
      />
      <p>
        Apple Inc. is an American multinational technology company headquartered
        in Cupertino, California. As of March 2023, Apple is the world's largest
        company by market capitalization, and with US$394.3 billion the largest
        technology company by 2022 revenue. As of June 2022, Apple is the
        fourth-largest personal computer vendor by unit sales; the largest
        manufacturing company by revenue; and the second-largest mobile phone
        manufacturer in the world. It is considered one of the Big Five American
        information technology companies, alongside Alphabet (parent company of
        Google), Amazon, Meta, and Microsoft.
      </p>
      <p>
        Apple was founded as Apple Computer Company on April 1, 1976, by Steve
        Wozniak, Steve Jobs and Ronald Wayne to develop and sell Wozniak's Apple
        I personal computer. It was incorporated by Jobs and Wozniak as Apple
        Computer, Inc. in 1977. The company's second computer, the Apple II,
        became a best seller and one of the first mass-produced microcomputers.
        Apple went public in 1980 to instant financial success. The company
        developed computers featuring innovative graphical user interfaces,
        including the 1984 original Macintosh, announced that year in a
        critically acclaimed advertisement called "1984". By 1985, the high cost
        of its products, and power struggles between executives, caused
        problems. Wozniak stepped back from Apple and pursued other ventures,
        while Jobs resigned and founded NeXT, taking some Apple employees with
        him.
      </p>
      <p>
        As the market for personal computers expanded and evolved throughout the
        1990s, Apple lost considerable market share to the lower-priced duopoly
        of the Microsoft Windows operating system on Intel-powered PC clones
        (also known as "Wintel"). In 1997, weeks away from bankruptcy, the
        company bought NeXT to resolve Apple's unsuccessful operating system
        strategy and entice Jobs back to the company. Over the next decade, Jobs
        guided Apple back to profitability through a number of tactics including
        introducing the iMac, iPod, iPhone and iPad to critical acclaim,
        launching the "Think different" campaign and other memorable advertising
        campaigns, opening the Apple Store retail chain, and acquiring numerous
        companies to broaden the company's product portfolio. When Jobs resigned
        in 2011 for health reasons, and died two months later, he was succeeded
        as CEO by Tim Cook.
      </p>
      <p>
        Apple became the first publicly traded U.S. company to be valued at over
        $1 trillion in August 2018, then at $2 trillion in August 2020, and at
        $3 trillion in January 2022. In June 2023, it was valued at just over $3
        trillion. The company receives criticism regarding the labor practices
        of its contractors, its environmental practices, and its business
        ethics, including anti-competitive practices and materials sourcing.
        Nevertheless, the company has a large following and enjoys a high level
        of brand loyalty. It has also been consistently ranked as one of the
        world's most valuable brands.
      </p>

      <div class="products">
        <h2>Products</h2>
        <hr />
        <div class="product">
          <h3>iPhone</h3>
          <p>
            The iPhone is Apple's line of smartphones, which run the iOS
            operating system. The first iPhone was unveiled by Steve Jobs on
            January 9, 2007. Since then, new models have been released annually.
            When it was introduced, its multi-touch screen was described as
            "revolutionary" and a "game-changer" for the mobile phone industry.
            The device has been credited with creating the app economy.
          </p>
          <p>
            As of 2022, the iPhone has 15% market share, yet represents 50% of
            global smartphone revenues, with Android phones accounting for the
            rest.[181] The iPhone has generated large profits for the company,
            and is credited with helping to make Apple one of the world's most
            valuable publicly traded companies.
          </p>
        </div>
        <div class="product">
          <h3>Mac</h3>
          <p>
            The Mac is Apple's family of personal computers. Macs are known for
            their ease of use[180] and distinctive aluminium, minimalist
            designs. Macs have been popular among students, creative
            professionals, and software engineers. The current lineup consists
            of the MacBook Air and MacBook Pro laptops, and the iMac, Mac mini,
            Mac Studio and Mac Pro desktop computers.
          </p>
          <p>
            Often described as a walled garden, Macs use Apple silicon chips,
            run the macOS operating system, and include Apple software like the
            Safari web browser, iMovie for home movie editing, GarageBand for
            music creation, and the iWork productivity suite. Apple also sells
            pro apps: Final Cut Pro for video production, Logic Pro for
            musicians and producers, and Xcode for software developers.
          </p>
          <p>
            Apple also sells a variety of accessories for Macs, including the
            Pro Display XDR, Apple Studio Display, Magic Mouse, Magic Trackpad,
            and Magic Keyboard.
          </p>
        </div>
      </div>
    </div>
  </div>
  <h5>Reference from https://codepen.io/bear320/pen/jOdXQGx</h5>
</template>
<style scoped>
.timeline-scroll-container {
  position: relative;
  overflow: auto;
  width: 80%;
  height: 40vh;
}

img {
  width: 400px;
}

@keyframes progress {
  from {
    transform: scaleX(0);
  }
  to {
    transform: scaleX(1);
  }
}

.timeline-scroll-container {
  scroll-timeline: --progress block;
}

.progress {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 0.5rem;
  background-color: #f08080;
  transform-origin: 0 50%;
  animation: progress auto linear;
  animation-timeline: --progress;
}

.container {
  margin: auto;
  padding: 1rem;
  max-width: 900px;

  img {
    width: 100%;
  }

  p {
    text-align: justify;
  }
}
</style>
