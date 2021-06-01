<script>
  import Header from '$lib/Header.svelte'
  import {signup, login, logout} from '../database'
  import { user } from '../stores'
</script>

<Header />

<section class="section">
  <button class="button" on:click={signup}>Signup</button>
  <button class="button" on:click={login}>Login</button>
  <button class="button" on:click={logout}>Logout</button>
</section>

<label class=label>
  user.uid:
  <textarea class="input" readonly>{$user.uid}</textarea>
</label>

<label class="label">
  user.email:
  <textarea class="input" readonly>{$user.email}</textarea>
</label>