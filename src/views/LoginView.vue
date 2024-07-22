<template>
  <div>
    <button @click="signInWithGoogle">Login with Google</button>
  </div>
</template>

<script setup>
import { getAuth, GoogleAuthProvider, signInWithPopup } from "firebase/auth";
import { useRouter } from "vue-router";

const router = useRouter();

const signInWithGoogle = () => {
  const provider = new GoogleAuthProvider();
  signInWithPopup(getAuth(), provider)
    .then((result) => {
      router.push("/home");
      console.log(result.user);
    })
    .catch((error) => {
      console.log(error);
    });
};
</script>
