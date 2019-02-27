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
  <div>
    <p id="project-staff-heading">
      The assigned Project Managers for this Project will be able to perform any
      administrative or auditing task related to this Project. Sitewide
      Administrators are automatically considered Managers of every Project. To
      learn more about Projects and Managers, please see
      <doc-link to="central-projects/#project-managers">this article</doc-link>.
    </p>
  </div>
</template>

<script>
export default {
  name: 'ProjectStaff',
  // Setting this in order to ignore attributes from ProjectShow that are
  // intended for other project components.
  inheritAttrs: false
};
</script>

<style lang="scss">
@import '../../../assets/scss/variables';

#project-staff-heading {
  margin-bottom: 20px;
  max-width: $max-width-p;
}
</style>
