<!--
Copyright 2017 ODK Central Developers
See the NOTICE file at the top-level directory of this distribution and at
https://github.com/opendatakit/central-frontend/blob/master/NOTICE.

This file is part of ODK Central. It is subject to the license terms in
the LICENSE file found in the top-level directory of this distribution and at
https://www.apache.org/licenses/LICENSE-2.0. No part of ODK Central,
including this file, may be copied, modified, propagated, or distributed
except according to the terms contained in the LICENSE file.
-->
<template>
  <modal :state="state" :hideable="!awaitingResponse" backdrop
    @hide="$emit('hide')">
    <template slot="title">Reset Password</template>
    <template slot="body">
      <p class="modal-introduction">
        Once you click <strong>Reset Password</strong> below, the password for
        {{ user.email }} will be immediately invalidated. An email will be sent
        to {{ user.email }} with instructions on how to proceed.
      </p>
      <div class="modal-actions">
        <button id="user-reset-password-button" :disabled="awaitingResponse"
          type="button" class="btn btn-primary" @click="resetPassword">
          Reset password <spinner :state="awaitingResponse"/>
        </button>
        <button :disabled="awaitingResponse" type="button" class="btn btn-link"
          @click="$emit('hide')">
          Close
        </button>
      </div>
    </template>
  </modal>
</template>

<script>
import request from '../../mixins/request';

export default {
  name: 'UserResetPassword',
  mixins: [request()],
  props: {
    state: {
      type: Boolean,
      default: false
    },
    user: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      requestId: null
    };
  },
  methods: {
    resetPassword() {
      const data = { email: this.user.email };
      this
        .post('/users/reset/initiate?invalidate=true', data)
        .then(() => {
          this.$emit('hide');
          this.$alert().blank();
          this.$emit('success');
        })
        .catch(() => {});
    }
  }
};
</script>
