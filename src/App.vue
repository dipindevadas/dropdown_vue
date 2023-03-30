<template>


 

  <div class="body bg-slate-100" >
    <header>
      <div class="nav-area flex">
        
        <nav>
          <ul class="menus">
            <button @mouseenter="openDropdown()" class=" text-white text-xl  font-bold p-1 rounded-md px-32 font-serif"  >SHOP BY CATEGORY </button>
          </ul>
          
        </nav>
        <div class='offer_section ml-6' ><i class="fa-solid fa-tag text-red-700 text-2xl "></i> <span class='offer_text font-semibold text-gray-500 text-lg'>OFFERS</span></div>

        
      </div>
    </header>
   
   
    <div class=" flex ml-10 " @mouseleave="closeAll()">
      <ul class="dropdown-menu p-1" v-if="isDropdownOpen" >
        <li class=" flex hover:bg-gray-200 cursor-pointer font-medium font-serif text-gray-700 mt-1 bg-white " v-for="item in items" :key="item.id"   @mouseenter="Submenu1(item)">{{ item.title }} </li>
      </ul>
        
      <ul  class="dropdown-submenu  p-1"  v-if="isSubmenuDropdown"  >
        <li class="hover:bg-gray-200 cursor-pointer font-medium font-serif text-gray-700 mt-1 bg-white"  v-for="subItem in subItems" :key="subItem.id"  @mouseenter="setsecondSubmenu(subItem)">{{ subItem.name }}
        </li>
 

      </ul>
      <ul  class="dropdown-submenu1 p-1 "  v-if="isSubmenuSecDropdown">
        <li class="hover:bg-gray-200 cursor-pointer font-medium font-serif text-gray-700 mt-1 bg-white" v-for="secsubItem in secSubItems" :key="secsubItem.id" >{{ secsubItem.value }}</li>
      </ul>
    </div>
  </div>
</template>
  
  <script setup >
  import { ref } from "vue";
  

  
  const items = [
    {
      title: "Fruits & Vegitables",
      id: 1,
      submenu: [
        {
          name: "Fresh Vegitables",
          id: 13,
          submenu2: [
            {
              value: "Potato, Onion & Tomato",
              id: 31,
            },
            {
              value: "Cucumber& Capsicum",
              id: 32,
            },
            {
              value: "Leafy vegetables",
              id: 33,
            },
            {
              value: "Root Vegitables",
              id: 34,
            },
            {
              value: "Bean,Brinjals & Okra",
              id: 35,
            },
            {
              value: "Cabbage & Cauliflower",
              id: 36,
            },
            {
              value: "Gourd,Pumpkin,Drumstick",
              id: 37,
            },
            {
              value: "Speciality",
              id: 38,
            },
          ],
        },
        {
          name: "Hearbs & Seasonings",
          id: 14,
        },
        {
          name: "Fresh Fruits",
          id: 15,
        },
        {
          name: "Organic Fruits & Vegitables",
          id: 16,
        },
        {
          name: "Cuts & Sprouts",
          id: 17,
        },
        {
          name: "Exotic Fruits & veggies",
          id: 18,
        },
        {
          name: "Flower Bouquets, Bunches",
          id: 19,
        },
      ],
    },
    {
      title: "Foodgrains,oil & masala",
      id: 2,
      submenu: [
        {
          name: "Pam oil",
          id: 20,
        },
        {
          name: "chat masala",
          id: 21,
        },
        {
          name: "coconut oil ",
          id: 22,
        },
        {
          name: " Fruits  ",
          id: 23,
        },
        {
          name: "Cuts ",
          id: 24,
        },
        {
          name: "Exotic& ",
          id: 25,
        },
        {
          name: "Flower",
          id: 26,
        },
      ],
    },
    {
      title: "Bakery,Cakes & Dairy",
      id: 3,
      submenu: [
        {
          name: "black forest cake",
          id: 27,
        },
        {
          name: "chocalate ice cream",
          id: 28,
        },
        {
          name: "biscuts,snacks  ",
          id: 29,
        },
      ],
    },
    {
      title: "Beverages",
      id: 4,
      submenu: [
        {
          name: "grape vine",
          id: 30,
        },
        {
          name: "fresh juice",
          id: 31,
        },
        {
          name: "cool drinks  ",
          id: 32,
        },
      ],
    },
    {
      title: "Snacks & Branded Foods",
      id: 5,
      submenu: [
        {
          name: "Snacks",
          id: 33,
        },
        {
          name: "chicken noodles",
          id: 34,
        },
        {
          name: "egg cutlet  ",
          id: 35,
        },
      ],
    },
    {
      title: "Beauty & Hygiene",
      id: 6,
      submenu: [
        {
          name: "Beauty",
          id: 36,
        },
        {
          name: " Hygiene",
          id: 37,
        },
      ],
    },
    {
      title: "Cleaning & Household",
      id: 7,
      submenu: [
        {
          name: "Cleaning",
          id: 38,
        },
        {
          name: " Household",
          id: 39,
        },
      ],
    },
    {
      title: "Kitchen,Garden & Pets",
      id: 8,
      submenu: [
        {
          name: "Kitchen",
          id: 40,
        },
        {
          name: " Garden",
          id: 41,
        },
      ],
    },
    {
      title: "Eggs,Meat & Fish",
      id: 9,
      submenu: [
        {
          name: "egg",
          id: 40,
        },
        {
          name: " fish",
          id: 41,
        },
      ],
    },
    {
      title: "Gourment & World Food",
      id: 10,
      submenu: [
        {
          name: "gourment",
          id: 40,
        },
        {
          name: " food",
          id: 41,
        },
      ],
    },
    {
      title: "Baby Care",
      id: 11,
      submenu: [
        {
          name: "baby",
          id: 40,
        },
        {
          name: " care",
          id: 41,
        },
      ],
    },
    {
      title: "View All",
      id: 12,
    },
  ];
  
  const subItems = ref([]);
  const secSubItems = ref([]);
  
  let isDropdownOpen = ref(false);
  let isSubmenuDropdown = ref(false);
  let isSubmenuSecDropdown = ref(false);
  
  function openDropdown() {
    console.log(items);
    isDropdownOpen.value = true;
  }
  
  function Submenu1(item) {
    // console.log(items);
    subItems.value = item.submenu;
    isSubmenuDropdown.value = true;
  }
  
  function setsecondSubmenu(subItem) {
    secSubItems.value = subItem.submenu2;
    isSubmenuSecDropdown.value = true;
  }
  
 
  
  function closeAll() {
    isDropdownOpen.value = false;
    isSubmenuDropdown.value = false;
    isSubmenuSecDropdown.value = false;
  }
  
  
  </script>

  <style>
  
  header {
    box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.07), 0 1px 2px 0 rgba(0, 0, 0, 0.05);
    
    width: 100%;
  
    
  }
  
  .nav-area {
    width: 100%;
    margin: 0 auto;
    padding: 10px 20px;
    background-color: #fff;
    
  }
  
  
  .menus {
    border-radius: 5px;
    background-color: #84cc16;
  }
  
  li {
    
    width: 370px;
    list-style: none;
    padding: 0.5rem 0;
    background-color: #fff;
    border-radius: 0.5rem;
    box-shadow: 0 10px 15px -3px rgba(46, 41, 51, 0.08),
    0 4px 6px -2px rgba(71, 63, 79, 0.16);
    font-size: 1.2rem;
  }
  
</style>