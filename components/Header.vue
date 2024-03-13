<template>
  <div class="nav-container">
    <div class="navbar">
      <div class="logo">
        <div class="flex items-center">
          <img class="w-10" src="../assets/inner-logo.png" alt="mannit-logo" />
        </div>
      </div>
      <div class="container">
        <span class="custom-text">Ahamed's Apple</span>
      </div>
      <div class="menu lg:flex">
        <ul class="flex gap-50 items-center font-medium text-black">
          <li class="hover:text-[#25A449]">
            <NuxtLink to="/home" class="custom-link">Home</NuxtLink>
          </li>
          <li class="hover:text-[#25A449]" @click="toggleDropdown('report')">
            Reports <span>&#9662;</span>
            <ol v-if="activeDropdown === 'report'" class="dropdown">
              <li>
                <NuxtLink class="custom-link" to="/chatbotreport">Chatbot</NuxtLink>
              </li>
              <li>
                <NuxtLink class="custom-link" to="/enquiryReport">Enquiry</NuxtLink>
              </li>
            </ol>
          </li>
          <li class="hover:text-[#25A449]" @click="toggleDropdown('profile')">
            Profile <span>&#9662;</span>
            <ol v-if="activeDropdown === 'profile'" class="dropdown">
              <li>
                <NuxtLink class="custom-link" to="/profile">Change Password</NuxtLink>
              </li>
              <li>
                <NuxtLink v-if="userRole === 'admin'" class="custom-link" to="/addUser">Add User</NuxtLink>
              </li>
            </ol>
          </li>
        </ul>
      </div>
      <div class="logout-button-container">
        <nuxt-link to="/login">
          <button type="submit" class="back-button">
            <svg width="60" height="0" viewBox="0 0 90 90" fill="none" xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink">
              <rect width="90" height="90" fill="url(#pattern0)" />
              <defs>
                <pattern id="pattern0" patternContentUnits="objectBoundingBox" width="1" height="1">
                  <use xlink:href="#image0_762_77" transform="scale(0.0111111)" />
                </pattern>
                <image id="image0_762_77" width="70" height="90"
                  xlink:href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFoAAABaCAYAAAA4qEECAAAACXBIWXMAAAsTAAALEwEAmpwYAAACJklEQVR4nO3dvW4TQRTF8ROKABIvQHjD8FGSNwCJhoKKinegQDxBIAWEl0BCogIHRVR/tNJECijYa2dnfXxyf/2O5x6tZm3P1axUSimllFJKKQmA28AT4CNwxu44a3N+BOzLGfAA+MLuOx1qkfGdnBDyhc+Wd3ZbLtI8lBvghDwf5AZYkGchN4SSG0LJDaHkhlByQyi5IZTcEEpuCCU3hJIbQskNoeSGUHJDKLkhlNwQSm4IpXG13wVetw3e78CLYWuvgp4+6CHkf73rEjahtLruvSW7S9OHTSiNq/3nkiGmDZtQGlf7yxXDTBc2oTS+p2UIs3/YhNL4+veBtyuGew/cqaCvsObN1j9sQmn9HPqGTShtlkW/sAmlDXULm1C6hi5hM6/fwFPg4DpBGNU1/qsf8zrqHfAW6nruNqHB/e4Jz1/XN7cJMceSsYW6vrpNKHXpeOY2oYuH4VE9DIPohn+9m41VyBX03+on+Aa0pvpTaUNWIbcPiSSnkG960NRW1mxBv1oxTG3OrjIi5FvAryVDVLvBhEGf/+fyaqCZeOl4c8Wl1RLWIeh7Lezz1h42NNRUk+PUQV8KfE+9EUpuCCU3hJIbQskNoeSGUHJDKLkhlNwQSm4IJTeEkhtCyQ2h5IZQchN6COwPuWnHtqc5lhvgMXkO5ab1Ngxn46f4ZHn0/KWXKZyGhHwgZ601anjFxvGOPSAXbc6HtndyKaWUUkoppWhL/gA8W92XIF47ywAAAABJRU5ErkJggg==" />
              </defs>
            </svg>
          </button>
        </nuxt-link>
      </div>
      <div class="menu-icon" @click="toggleMenu">
        <img src="../assets/menu.png" alt="menu" v-if="!showMenu" class="cursor-pointer w-6 h-6" />
        <img src="../assets/close.png" alt="close" v-else class="cursor-pointer w-6 h-6" />
      </div>
    </div>
    <div class="responsive-menu" :class="{ 'active': showMenu }">
      <li class="flex flex-col items-center space-y-4 list-none">
      <li class="text-[#25A449]">
        <NuxtLink class="custom-link" to="/home">Home</NuxtLink>
      </li>
      <li class="text-[#25A449]" @click="toggleDropdown('report')">
        Reports <span>&#9662;</span>
        <ol v-if="activeDropdown === 'report'" class="dropdown">
          <li>
            <NuxtLink class="custom-link" to="/chatbotreport">Chatbot</NuxtLink>
          </li>
          <li>
            <NuxtLink class="custom-link" to="/enquiryReport">Enquiry</NuxtLink>
          </li>
        </ol>
      </li>
      <li class="text-[#25A449]" @click="toggleDropdown('profile')">
        Profile <span>&#9662;</span>
        <ol v-if="activeDropdown === 'profile'" class="dropdown">
          <li>
            <NuxtLink class="custom-link" to="/profile">Change Password</NuxtLink>
          </li>
          <li>
            <NuxtLink v-if="userRole === 'admin'" class="custom-link" to="/addUser">Add User</NuxtLink>
          </li>
        </ol>
      </li>
      <div class="logout-button-container">
        <nuxt-link to="/login">
          <button type="submit" class="back-button-responsive">
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect width="20" height="20" fill="#8BD600" />
              <path
                d="M13.5832 9.67453C13.5041 9.60431 13.4022 9.56763 13.2981 9.57179C13.194 9.57596 13.0952 9.62067 13.0215 9.697C12.9478 9.77332 12.9046 9.87564 12.9006 9.9835C12.8966 10.0914 12.932 10.1968 12.9998 10.2788L14.3984 11.6974H12.2756V12.5545H14.3984L12.9998 14.0374C12.9565 14.0758 12.9213 14.1231 12.8964 14.1763C12.8716 14.2294 12.8576 14.2873 12.8554 14.3464C12.8532 14.4054 12.8628 14.4642 12.8836 14.5192C12.9045 14.5742 12.936 14.6242 12.9763 14.6659C13.0167 14.7077 13.0649 14.7404 13.118 14.7619C13.1711 14.7835 13.2279 14.7934 13.2849 14.7912C13.3419 14.7889 13.3978 14.7744 13.4491 14.7487C13.5005 14.723 13.5461 14.6865 13.5832 14.6417L15.9998 12.156L13.5832 9.67453Z"
                fill="white" />
              <path
                d="M11.4483 4H4.82759C4.6081 4 4.3976 4.09031 4.24239 4.25105C4.08719 4.4118 4 4.62981 4 4.85714V15.1429C4 15.3702 4.08719 15.5882 4.24239 15.7489C4.3976 15.9097 4.6081 16 4.82759 16H11.4483C11.6678 16 11.8783 15.9097 12.0335 15.7489C12.1887 15.5882 12.2759 15.3702 12.2759 15.1429V12.5714H8.39862C8.28888 12.5714 8.18363 12.5263 8.10603 12.4459C8.02842 12.3655 7.98483 12.2565 7.98483 12.1429C7.98483 12.0292 8.02842 11.9202 8.10603 11.8398C8.18363 11.7594 8.28888 11.7143 8.39862 11.7143H12.2759V4.85714C12.2759 4.62981 12.1887 4.4118 12.0335 4.25105C11.8783 4.09031 11.6678 4 11.4483 4Z"
                fill="white" />
            </svg>
          </button>
        </nuxt-link>
      </div>
      </li>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showMenu: false,
      activeDropdown: null,
      showProfileDropdown: false,
    };
  },
  methods: {
    toggleMenu() {
      this.showMenu = !this.showMenu;
    },
    closeMenu() {
      this.showMenu = false;
    },
    toggleDropdown(dropdown) {
      if (this.activeDropdown === dropdown) {
        this.activeDropdown = null;
      } else {
        this.activeDropdown = dropdown;
      }
    },
    toggleDropdown(dropdown) {
      if (this.activeDropdown === dropdown) {
        this.activeDropdown = null;
      } else {
        this.activeDropdown = dropdown;
      }
    },
  },
};
</script>

<style scoped>
.logout-button-container {
  display: flex;
  align-items: center;
  margin-left: auto;
}

.back-button {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: transparent;
  border: none;
  cursor: pointer;
  margin-right: 77px;
}

.back-button svg {
  width: 40px;
  height: 40px;
  background-color: #8db600;
}

.custom-link {
  text-decoration: none;
  color: black;
}

.custom-link:hover {
  color: #8db600;
}

.responsive-menu .dropdown {
  padding: 0;
  margin: 0;
}

.responsive-menu .dropdown li {
  padding: 16px;
}

.responsive-menu .dropdown li:hover {
  background-color: #fdd116;
  color: #333;
}

.dropdown {
  list-style: none;
  position: absolute;
  background-color: #ffffff;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  z-index: 1000;
  color: black;
}

.dropdown ol {
  list-style: none;
  padding: 0;
  /* Remove padding */
  margin: 0;
  /* Remove margin */
}

.dropdown li {
  padding: 10px;
  color: black;
}



.nav-container {
  width: 100%;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #fff;
  border-bottom: 3px solid #8db600;
  height: 70px;
  padding: 0 20px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.logo img {
  width: 100%;
  max-width: 62px;
}

.menu {
  display: flex;
}

.menu ul {
  list-style: none;
  display: flex;
  gap: 40px;
}

.menu li {
  color: black;
  font-size: 20px;
}


.menu li:hover {
  color: #8db600;
}

.menu-icon img {
  display: none;
  width: 30px;
  height: 30px;
}

.responsive-menu {
  display: none;
  flex-direction: column;
  position: absolute;
  top: 79px;
  width: 100%;
  background-color: #fff;
  /* Set the default background color to white */
  border-bottom: 3px solid #8db600;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.responsive-menu.active {
  display: flex;
  list-style: none;
  align-items: center;
  background-color: #fff;
  z-index: 1000;
}


.container {
  display: flex;
  align-items: center;
  margin-right: 305px;
}

.custom-text {
  margin-left: 9px;
  font-size: 1.25rem;
  /* equivalent to text-lg in some cases */
  font-weight: bold;
}

@media screen and (max-width: 1048px) {

  .custom-text {
    margin-left: 8px;
    font-size: 1.25rem;
    font-weight: bold;
  }

}

@media screen and (max-width: 768px) {
  .container {
    display: flex;
    align-items: center;
    margin-right: 1px;
  }

  .custom-text {
    margin-left: 8px;
    font-size: 1.25rem;
    font-weight: bold;
  }

  .menu {
    display: none;
  }

  .menu-icon img {
    display: block;
    width: 30px;
    height: 30px;
  }

  .back-button {
    display: none;
  }

  .back-button-responsive {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: transparent;
    border: none;
    cursor: pointer;
    margin-left: 16px;
  }

  .back-button-responsive svg {
    width: 30px;
    height: 30px;
    background-color: #8db600;
  }

  .logout-button-container {
    display: flex;
    align-items: center;
    margin-left: auto;
  }
}

@media screen and (max-width: 600px) {
  .container {
    display: flex;
    align-items: center;
  }

  .custom-text {
    margin-left: 34px;
    font-size: 1.25rem;
    font-weight: bold;
  }

  .responsive-menu {
    font-size: 25px;
  }

  .back-button-responsive {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: transparent;
    border: none;
    cursor: pointer;
    margin-left: 16px;
  }

  .back-button-responsive svg {
    width: 15px;
    height: 15px;
    background-color: #8db600;
  }

  .logout-button-container {
    display: flex;
    align-items: center;
    margin-left: 16px;
  }
}
</style>
