<script>
  import { createEventDispatcher } from 'svelte';
  import { getCookie, removeAllCookies, setCookie } from './scripts/cookies.js';

  const dispatch = createEventDispatcher();

  const cookiesAllowed = getCookie('cookiesAllowed');

  function closeSettings(allowCookies) {
    if (allowCookies) {
      setCookie('cookiesAllowed', true);
    } else {
      if (cookiesAllowed) {
        removeAllCookies();
      }
    }
    dispatch('close');
  }
</script>

<div class="settings-wrapper">
  <div class="content">
    <div align="center">
      <img alt="Solidity Logo" src="https://img.icons8.com/?size=100&id=HOqGCOyHDbd4&format=png&color=000000">
    </div>
    <h1>Solidity quiz</h1>
    <p>
      Hicimos este quiz para probar qué tanto vamos aprendiendo en Solidity 🤓.
      Empieza fácil pero se irá poniendo más difícil. 
    </p>
    <p>
      No te preocupes si algunos conceptos no te hacen sentido, solo respira, 
      pregunta, vuelve a intentarlo, no pasa nada, estamos aquí para aprender! 📚
    </p>
    <p>
      La app puede guardar tus respuestas localmente mediante cookies para que continues
      jugando en otra ocasión. Si quieres permitírselo, solo presiona el botón verde. ✅
    </p>
    <p>LFG! 🚀🚀</p>
    <div class="button-wrapper">
      <button
        class="deny plausible-event-name=Deny+Cookies"
        on:click={() => closeSettings()}
        >sin cookies{#if cookiesAllowed}*{/if}</button
      >
      <button
        class="allow plausible-event-name=Allow+Cookies"
        on:click={() => closeSettings(true)}>permitir</button
      >
    </div>
    {#if cookiesAllowed}
      <p>* Your current score will also be cleared! ⚠️</p>
    {/if}
    <a
      href="https://github.com/garosan/solidity-quiz"
      target="_blank"
      rel="noopener">repo fuente</a
    >
  </div>
</div>

<style>
  .settings-wrapper {
    width: 100%;
    height: 100%;
    position: fixed;
    z-index: 1000;
    background-color: white;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .content {
    display: flex;
    max-width: 400px;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .content > *:not(:last-child) {
    margin-bottom: 16px;
    text-align: center;
  }

  .button-wrapper {
    width: 100%;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    align-items: center;
  }

  button {
    width: 150px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 16px;
    border-radius: 8px;
    text-transform: uppercase;
    cursor: pointer;

    box-shadow: 0px 2px 4px -1px rgb(0 0 0 / 20%),
      0px 4px 5px 0px rgb(0 0 0 / 14%), 0px 1px 10px 0px rgb(0 0 0 / 12%);
  }

  .allow {
    background-color: rgba(0, 90, 0, 0.75);
    border: rgb(0, 100, 0) 2px solid;
    color: white;
  }

  .deny {
    background-color: white;
    border: rgb(100, 0, 0) 2px solid;
  }
</style>
