<script>
  let partyScores = {
    FRP: 0,
    høyre: 0,
    KRF: 0,
    venstre: 0,
    MDG: 0,
    SP: 0,
    AP: 0,
    SV: 0,
    rødt: 0,
  };

  function handleCheck(event) {
    if (event.target.value === "enig") {
      partyScores.FRP += 1;
      partyScores.høyre += 1;
    } else if (event.target.value === "littEnig") {
      partyScores.venstre += 1;
      partyScores.KRF += 1;
    } else if (event.target.value === "littUenig") {
      partyScores.AP += 1;
    } else if (event.target.value === "uenig") {
      partyScores.MDG += 1;
      partyScores.SP += 1;
      partyScores.SV += 1;
      partyScores.rødt += 1;
    }
    console.log(partyScores);
  }

  $: innblandingØkonomi = "50";
  function handleSliderInput(event) {
    innblandingØkonomi = event.target.value;
    if (Number(innblandingØkonomi) > 75) {
      partyScores.AP += 1;
      partyScores.SP += 1;
      partyScores.rødt += 1;
      partyScores.SV += 1;
    } else if (Number(innblandingØkonomi) > 50) {
      partyScores.MDG += 1;
    } else if (Number(innblandingØkonomi) > 25) {
      partyScores.KRF += 1;
      partyScores.venstre += 1;
    } else if (Number(innblandingØkonomi) > 0) {
      partyScores.FRP += 1;
      partyScores.høyre += 1;
    }
    console.log(partyScores);
  }

  let utdanning = false;
  let helsetjenesten = false;
  let kollektivTransport = false;
  let sykkelveier = false;
  let lavereSkatter = false;

  function handleCheckboxInput(event) {
    if (event.target.id === "utdanning") {
      utdanning = event.target.checked;
    } else if (event.target.id === "helsetjenesten") {
      helsetjenesten = event.target.checked;
    } else if (event.target.id === "KollektivTransport") {
      kollektivTransport = event.target.checked;
    } else if (event.target.id === "sykkelveier") {
      sykkelveier = event.target.checked;
    } else if (event.target.id === "lavereSkatter") {
      lavereSkatter = event.target.checked;
    }

    if (utdanning) {
      partyScores.SP += 1;
      partyScores.AP += 1;
    }
    if (helsetjenesten) {
      partyScores.AP += 1;
      partyScores.SV += 1;
      partyScores.SP += 1;
    }
    if (kollektivTransport) {
      partyScores.venstre = +1;
      partyScores.SV += 1;
      partyScores.MDG += 1;
    }
    if (sykkelveier) {
      partyScores.MDG += 1;
      partyScores.venstre += 1;
    }
    if (lavereSkatter) {
      partyScores.høyre += 1;
      partyScores.FRP += 1;
      partyScores.venstre += 1;
    }

    console.log(partyScores);
  }

  function skoleinntakHandleCheck(event) {
    if (event.target.value === "enig2") {
      partyScores.FRP += 1;
      partyScores.høyre += 1;
    } else if (event.target.value === "littEnig2") {
      partyScores.KRF += 1;
      partyScores.AP += 1;
      partyScores.SP += 1;
    } else if (event.target.value === "littUenig2") {
      partyScores.venstre += 1;
      partyScores.MDG += 1;
    } else if (event.target.value === "uenig2") {
      partyScores.SV += 1;
      partyScores.rødt += 1;
    }
    console.log(partyScores);
  }
  function sykkelveierHandleCheck(event) {
    if (event.target.value === "enig3") {
      partyScores.FRP += 1;
      partyScores.SP += 1;
    } else if (event.target.value === "littEnig3") {
      partyScores.KRF += 1;
      partyScores.høyre += 1;
    } else if (event.target.value === "littUenig3") {
      partyScores.rødt += 1;
      partyScores.AP += 1;
    } else if (event.target.value === "uenig3") {
      partyScores.SV += 1;
      partyScores.MDG += 1;
      partyScores.venstre += 1;
    }
    console.log(partyScores);
  }

  function ordningHandleCheck(event) {
    if (event.target.value === "dublinAvtalen") {
      partyScores.høyre += 1;
      partyScores.SP += 1;
      partyScores.venstre += 1;
      partyScores.KRF += 1;
    } else if (event.target.value === "frittAsylsøk") {
      partyScores.AP += 1;
      partyScores.rødt += 1;
      partyScores.SV += 1;
    } else if (event.target.value === "stoppForAsylsøkere") {
      partyScores.FRP += 1;
    } else if (event.target.value === "utsendingTilTransittland") {
      partyScores.MDG += 1;
    }
    console.log(partyScores);
  }

  function rusreformHandleCheck(event) {
    if (event.target.value === "enig4") {
      partyScores.høyre += 1;
      partyScores.venstre += 1;
      partyScores.MDG += 1;
      partyScores.rødt += 1;
      partyScores.AP += 1;
      partyScores.SV += 1;
    } else if (event.target.value === "littEnig4") {
      partyScores.FRP += 1;
      partyScores.SP += 1;
    } else if (event.target.value === "littUenig4") {
    } else if (event.target.value === "uenig4") {
      partyScores.KRF += 1;
    }
    console.log(partyScores);
  }

  function oljeHandleCheck(event) {
    if (event.target.value === "enig5") {
      partyScores.venstre += 1;
      partyScores.MDG += 1;
      partyScores.rødt += 1;
      partyScores.SV += 1;
    } else if (event.target.value === "littEnig5") {
      partyScores.KRF += 1;
    } else if (event.target.value === "littUenig5") {
    } else if (event.target.value === "uenig5") {
      partyScores.SP += 1;
      partyScores.FRP += 1;
      partyScores.høyre += 1;
      partyScores.AP += 1;
    }
    console.log(partyScores);
  }

  function updateResultDisplay() {
    const resultList = document.getElementById("resultList");
    resultList.innerHTML = "";

    const sortedParties = Object.keys(partyScores).sort(
      (a, b) => partyScores[b] - partyScores[a]
    );

    for (let i = 0; i < 3; i++) {
      const party = sortedParties[i];
      const score = partyScores[party];
      const listItem = document.createElement("li");
      listItem.textContent = `${party}: ${score} poeng`;
      resultList.appendChild(listItem);
    }
  }

  function showResults() {
    updateResultDisplay();
  }

  function toggleInfoBox() {
    const infoBox = document.getElementById("infoBox");
    infoBox.classList.toggle("active");
  }
</script>

<main>
  <h1>Valgomat</h1>

  <div id="myDiv">
    <h2>
      Regjeringen bør redusere skatter og reguleringer for å fremme økonomisk
      vekst
    </h2>

    <input
      type="radio"
      id="enig"
      name="valg"
      value="enig"
      on:change={handleCheck}
    />
    <label for="enig">Enig</label>

    <input
      type="radio"
      id="littEnig"
      name="valg"
      value="littEnig"
      on:change={handleCheck}
    />
    <label for="littEnig">litt enig</label>

    <input
      type="radio"
      id="littUenig"
      name="valg"
      value="littUenig"
      on:change={handleCheck}
    />
    <label for="littUenig">litt uenig</label>

    <input
      type="radio"
      id="uenig"
      name="valg"
      value="uenig"
      on:change={handleCheck}
    />
    <label for="uenig">Uenig</label>
  </div>

  <div id="myDiv">
    <h2>Hvor stor innblanding bør staten ha i økonomien?</h2>

    <input
      type="range"
      min="0"
      max="100"
      bind:value={innblandingØkonomi}
      on:change={handleSliderInput}
    />
    <label
      >{Number(innblandingØkonomi) <= 25
        ? "Lite statlig innblanding"
        : Number(innblandingØkonomi) >= 75
        ? "Mye statlig innblanding"
        : "Noe statlig innblanding"}</label
    >
  </div>

  <div id="myDiv">
    <h2>Hvilke tjenester bør staten fokusere mer på?</h2>
    <input
      type="checkbox"
      id="utdanning"
      bind:checked={utdanning}
      on:change={handleCheckboxInput}
    />
    <label for="utdanning">Utdanning</label>

    <input
      type="checkbox"
      id="helsetjenesten"
      bind:checked={helsetjenesten}
      on:change={handleCheckboxInput}
    />
    <label for="helsetjenesten">Helsetjenesten</label>

    <input
      type="checkbox"
      id="KollektivTransport"
      bind:checked={kollektivTransport}
      on:change={handleCheckboxInput}
    />
    <label for="kollektivTransport">Kollektiv transport</label>

    <input
      type="checkbox"
      id="sykkelveier"
      bind:checked={sykkelveier}
      on:change={handleCheckboxInput}
    />
    <label for="sykkelveier">Sykkelveier</label>

    <input
      type="checkbox"
      id="lavereSkatter"
      bind:checked={lavereSkatter}
      on:change={handleCheckboxInput}
    />
    <label for="lavereSkatter">Lavere skatter</label>
  </div>

  <div id="myDiv">
    <h2>Skoleinntaket bør kun basere seg på karakterer</h2>
    <input
      type="radio"
      id="enig2"
      name="valg2"
      value="enig2"
      on:change={skoleinntakHandleCheck}
    />
    <label for="enig2">Enig</label>

    <input
      type="radio"
      id="littEnig2"
      name="valg2"
      value="littEnig2"
      on:change={skoleinntakHandleCheck}
    />
    <label for="littEnig2">litt enig</label>

    <input
      type="radio"
      id="littUenig2"
      name="valg2"
      value="littUenig2"
      on:change={skoleinntakHandleCheck}
    />
    <label for="littUenig2">litt uenig</label>

    <input
      type="radio"
      id="uenig2"
      name="valg2"
      value="uenig2"
      on:change={skoleinntakHandleCheck}
    />
    <label for="uenig2">Uenig</label>
  </div>

  <div id="myDiv">
    <h2>
      Det fjernes for mange parkeringsplasser for å gi plass til sykkelveier
    </h2>

    <input
      type="radio"
      id="enig3"
      name="valg3"
      value="enig3"
      on:change={sykkelveierHandleCheck}
    />
    <label for="enig3">Enig</label>

    <input
      type="radio"
      id="littEnig3"
      name="valg3"
      value="littEnig3"
      on:change={sykkelveierHandleCheck}
    />
    <label for="littEnig3">litt enig</label>

    <input
      type="radio"
      id="littUenig3"
      name="valg3"
      value="littUenig3"
      on:change={sykkelveierHandleCheck}
    />
    <label for="littUenig3">litt uenig</label>

    <input
      type="radio"
      id="uenig3"
      name="valg3"
      value="uenig3"
      on:change={sykkelveierHandleCheck}
    />
    <label for="uenig3">Uenig</label>
  </div>

  <div id="myDiv">
    <h2>Hvilken ordning skal gjelde for asylsøkere i Norge?</h2>
    <select id="ordningk" on:change={ordningHandleCheck}>
      <option value="">velg en ordning</option>
      <option value="dublinAvtalen">Dublin-avtalen</option>
      <option value="frittAsylsøk">Fritt asylsøk</option>
      <option value="stoppForAsylsøkere">Stopp for asylsøkere</option>
      <option value="utsendingTilTransittland"
        >Utsending til transittland</option
      >
    </select>
    <button on:mouseenter={toggleInfoBox} on:mouseleave={toggleInfoBox}
      >Vis info</button
    >
  </div>

  <div id="infoBox">
    <ul>
      <li>
        Dublinavtalen er en avtale inngått mellom medlemslandene i EU som
        regulerer hvilket EU-land som er ansvarlig for å vurdere en asylsøknad
        fra en person som søker beskyttelse i EU.
      </li>
      <li>
        Prinsippet om fritt asylsøk innebærer at en person har rett til å søke
        asyl i et annet land dersom de føler seg forfulgt eller truet i sitt
        eget land. 
      </li>
      <li>
        Dette refererer vanligvis til politikken der enkelte land midlertidig eller permanent nekter å akseptere nye asylsøknader eller å behandle dem på sitt territorium.
      </li>
      <li>
        Dette konseptet innebærer at en asylsøker eller flyktning blir sendt til et tredjeland (et transittland) i stedet for å få asyl i det landet de først søkte beskyttelse i.
      </li>
    </ul>
  </div>

  <div id="myDiv">
    <h2>Oslo bør få en lokal rusreform</h2>

    <input
      type="radio"
      id="enig4"
      name="valg4"
      value="enig4"
      on:change={rusreformHandleCheck}
    />
    <label for="enig4">Enig</label>

    <input
      type="radio"
      id="littEnig4"
      name="valg4"
      value="littEnig4"
      on:change={rusreformHandleCheck}
    />
    <label for="littEnig4">litt enig</label>

    <input
      type="radio"
      id="littUenig4"
      name="valg4"
      value="littUenig4"
      on:change={rusreformHandleCheck}
    />
    <label for="littUenig4">litt uenig</label>

    <input
      type="radio"
      id="uenig4"
      name="valg4"
      value="uenig4"
      on:change={rusreformHandleCheck}
    />
    <label for="uenig4">Uenig</label>
  </div>

  <div id="myDiv">
    <h2>Norge bør slutte å lete etter olje og gass</h2>

    <input
      type="radio"
      id="enig5"
      name="valg5"
      value="enig5"
      on:change={oljeHandleCheck}
    />
    <label for="enig5">Enig</label>

    <input
      type="radio"
      id="littEnig5"
      name="valg5"
      value="littEnig5"
      on:change={oljeHandleCheck}
    />
    <label for="littEnig5">litt enig</label>

    <input
      type="radio"
      id="littUenig5"
      name="valg5"
      value="littUenig5"
      on:change={oljeHandleCheck}
    />
    <label for="littUenig5">litt uenig</label>

    <input
      type="radio"
      id="uenig5"
      name="valg5"
      value="uenig5"
      on:change={oljeHandleCheck}
    />
    <label for="uenig5">Uenig</label>
  </div>

  <button on:click={showResults}>Vis Resultater</button>

  <div id="results">
    <h2>Resultater:</h2>
    <ul id="resultList" />
  </div>
</main>

<style>
</style>
