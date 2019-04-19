<template>
  <div>
      <b-card header-tag='header' footer-tag='footer' style="color: black;" >
        <h6 slot='header' class='mb-0'>{{ detail.title }}</h6>
        <p>point : {{ detail.point }}</p>
        <p>Assigned To : {{ detail.assignedTo }}</p>
        <div v-if="detail.status=='Pre-Log'">
          <b-button href='' variant='danger' @click='remove' size="sm">Delete</b-button>
          <b-button href='' variant='primary' @click='todo' size="sm">To-Do</b-button>
        </div>
        <div v-if="detail.status=='To-Do'">
          <b-button href='' variant='primary' @click='prelog' size="sm">Pre-Log</b-button>
          <b-button href='' variant='danger' @click='remove' size="sm">Delete</b-button>
          <b-button href='' variant='primary' @click='ongoing' size="sm">On-Going</b-button>
        </div>
        <div v-if="detail.status=='On-Going'">
          <b-button href='' variant='primary' @click='todo' size="sm">To-Do</b-button>
          <b-button href='' variant='danger' @click='remove' size="sm">Delete</b-button>
          <b-button href='' variant='primary' @click='finished' size="sm">Finished</b-button>
        </div>
        <div v-if="detail.status=='Finished'">
          <b-button href='' variant='primary' @click='ongoing' size="sm">On-Going</b-button>
          <b-button href='' variant='danger' @click='remove' size="sm">Delete</b-button>
        </div>
      </b-card>
    </div>
</template>
<script>
import db from '@/api/api';

export default {
  props: ['detail'],
  name: 'bebas',
  data() {
    return {
    };
  },
  methods: {
    remove() {
      db.collection('task').doc(this.detail.id).delete()
        .then(() => {
          console.log('Document successfully deleted!');
        })
        .catch((error) => {
          console.error('Error removing document: ', error);
        });
    },
    todo() {
      db.collection('task').doc(this.detail.id).set({ status: 'To-Do' }, { merge: true })
        .then((data) => {
          console.log(data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    prelog() {
      db.collection('task').doc(this.detail.id).set({ status: 'Pre-Log' }, { merge: true })
        .then((data) => {
          console.log(data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    ongoing() {
      db.collection('task').doc(this.detail.id).set({ status: 'On-Going' }, { merge: true })
        .then((data) => {
          console.log(data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    finished() {
      db.collection('task').doc(this.detail.id).set({ status: 'Finished' }, { merge: true })
        .then((data) => {
          console.log(data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style scoped>
.card-body{
  padding: 10px;
}
.card{
  margin: 10px 0;
}
</style>
