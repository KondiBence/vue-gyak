<template>
  <div class="page">
    <!-- Logo + cím -->
    <header class="header">
      <div class="logo-circle"></div>
      <h1 class="logo-text">VauTLS</h1>
    </header>

    <!-- Fő kártya -->
    <main class="card">
      <!-- Oldalsáv -->
      <aside class="sidebar">
        <div class="profile">
          <div class="avatar-wrapper">
            <div class="avatar-bg">
              <div class="avatar-shape"></div>
              <div class="avatar-shape2"></div>
            </div>
          </div>
          <div class="profile-text">
            <div class="profile-name">emily</div>
            <div class="profile-email">emily@example.com</div>
          </div>
        </div>

        <nav class="menu">
          <button class="menu-item active">Overview</button>
          <button class="menu-item">Users</button>
          <button class="menu-item">Settings</button>
        </nav>
      </aside>

      <!-- Tartalom -->
      <section class="content">
        <h2>Certificates</h2>

        <table class="cert-table">
          <thead>
            <tr>
              <th>User</th>
              <th>Name</th>
              <th>Created on</th>
              <th>Valid until</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="cert in certificates" :key="cert.id">
              <td>{{ cert.user }}</td>
              <td>{{ cert.name }}</td>
              <td>{{ cert.createdOn }}</td>
              <td>{{ cert.validUntil }}</td>
              <td class="actions">
                <button class="btn btn-blue" @click="downloadCertificate(cert)">
                  Download
                </button>
                <button class="btn btn-red" @click="deleteCertificate(cert.id)">
                  Delete
                </button>
              </td>
            </tr>
          </tbody>
        </table>

        <button class="btn btn-blue create-btn">
          Create New Certificate
        </button>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      certificates: [
        {
          id: 1,
          user: 'emily',
          name: 'surfboard',
          createdOn: '6/11/2025',
          validUntil: '6/11/2026'
        },
        {
          id: 2,
          user: 'paul',
          name: 'pixel8',
          createdOn: '6/11/2025',
          validUntil: '6/11/2026'
        },
        {
          id: 3,
          user: 'laura',
          name: 'tablet',
          createdOn: '6/11/2025',
          validUntil: '6/11/2027'
        }
      ]
    };
  },
  methods: {
    downloadCertificate(cert) {
      // itt majd lehet valódi letöltés
      alert(`Downloading certificate: ${cert.name}`);
    },
    deleteCertificate(id) {
      this.certificates = this.certificates.filter(c => c.id !== id);
    }
  }
};
</script>

<style scoped>
.page {
  min-height: 100vh;
  background: #e9f0f7;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI',
    sans-serif;
  padding: 40px 20px;
  box-sizing: border-box;
}

/* Fejléc / logo */
.header {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 30px;
}

.logo-circle {
  width: 70px;
  height: 70px;
  border-radius: 999px;
  background: radial-gradient(circle at 30% 30%, #ffffff 0, #8f9cf7 40%, #6dd5fa 100%);
  margin-right: 14px;
  position: relative;
}

.logo-circle::after {
  content: '';
  position: absolute;
  inset: 16px;
  border-radius: 999px;
  background: #e9f0f7;
}

.logo-text {
  font-size: 46px;
  font-weight: 500;
  letter-spacing: 2px;
  background: linear-gradient(90deg, #7a7af7, #6dd5fa);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

/* Fő kártya */
.card {
  max-width: 980px;
  margin: 0 auto;
  display: flex;
  background: #ffffff;
  border-radius: 18px;
  box-shadow: 0 18px 40px rgba(0, 0, 0, 0.08);
  overflow: hidden;
}

/* Oldalsáv */
.sidebar {
  width: 260px;
  background: #f4f6fb;
  padding: 24px;
  box-sizing: border-box;
}

.profile {
  display: flex;
  align-items: center;
  margin-bottom: 30px;
}

.avatar-wrapper {
  width: 70px;
  height: 70px;
  border-radius: 999px;
  overflow: hidden;
  background: #cfd6e8;
  margin-right: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.avatar-bg {
  width: 52px;
  height: 52px;
  border-radius: 50%;
  background: #2f3b55;
  position: relative;
}

.avatar-shape,
.avatar-shape2 {
  position: absolute;
  border-radius: 50%;
}

.avatar-shape {
  width: 24px;
  height: 24px;
  background: #ff7a59;
  top: 8px;
  left: 12px;
}

.avatar-shape2 {
  width: 18px;
  height: 18px;
  background: #16c79a;
  bottom: 10px;
  right: 8px;
}

.profile-name {
  font-weight: 600;
  text-transform: lowercase;
}

.profile-email {
  font-size: 13px;
  color: #6c7a89;
}

.menu {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.menu-item {
  border: none;
  border-radius: 8px;
  padding: 8px 12px;
  text-align: left;
  background: transparent;
  cursor: pointer;
  font-size: 14px;
}

.menu-item:hover {
  background: #dde3f5;
}

.menu-item.active {
  background: #cfd3ff;
}

/* Tartalom */
.content {
  flex: 1;
  padding: 24px 28px;
  box-sizing: border-box;
}

.content h2 {
  margin-top: 4px;
  margin-bottom: 18px;
  font-size: 24px;
}

/* Táblázat */
.cert-table {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 16px;
  font-size: 14px;
}

.cert-table thead {
  border-bottom: 1px solid #e0e0e0;
}

.cert-table th,
.cert-table td {
  padding: 10px 8px;
  text-align: left;
}

.cert-table tbody tr:nth-child(odd) {
  background: #f8f8f8;
}

.actions {
  display: flex;
  gap: 6px;
}

/* Gombok */
.btn {
  border: none;
  border-radius: 4px;
  padding: 6px 10px;
  font-size: 13px;
  cursor: pointer;
}

.btn-blue {
  background: #287bff;
  color: #ffffff;
}

.btn-blue:hover {
  background: #1e63ce;
}

.btn-red {
  background: #e74c3c;
  color: #ffffff;
}

.btn-red:hover {
  background: #c0392b;
}

.create-btn {
  margin-top: 8px;
  padding: 8px 16px;
}
</style>
