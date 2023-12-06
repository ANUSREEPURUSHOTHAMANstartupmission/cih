<script>

  export let menu_open;

  let y = 0;

  $: scrolled = y > 100;

  function findPos(obj) {
    var curtop = 0;
    if (obj.offsetParent) {
        do {
            curtop += obj.offsetTop;
        } while (obj = obj.offsetParent);
    return [curtop];
    }
  }

  const handleCyclo = (e) => {
    e.preventDefault()
    let button = e.target.closest('[data-target]');
    let target = button.getAttribute('data-target');
    let offset = button.getAttribute('data-offset');
    
    window.scroll({
      left:0,
      top:findPos(document.getElementById(target))-offset, 
      behavior:'smooth'
    });

    menu_open = !menu_open
    
  }

</script>

<svelte:window bind:scrollY={y}/>



<div id="navbar" class="w-64 min-h-screen  sm:w-full sm:min-h-0 sm:h-20 p-8 sm:py-3 text-white bg-[#567763]  left-0 top-0 
    sm:flex sm:items-center
     ease-in-out transition-all transform duration-300
    -translate-x-full sm:translate-x-0 fixed z-50 
     {menu_open?'translate-x-0':''} {scrolled?'md:bg-white':'md:bg-white'}
    ">
  


    <div class="flex bg-white top-4 absolute sm:hidden">    
      <button on:click="{()=> menu_open = !menu_open }" class="z-50 bg-[#003845] cursor-pointer fixed right-5 w-10 h-10 text-xl ml-auto transition duration-150 hover:shadow leading-none px-2 py-1 border border-solid border-transparent rounded bg-transparent block outline-none focus:outline-none" type="button">
        <span class="block absolute w-6 h-0.5 rounded-sm bg-black top-3 duration-500 { menu_open ? 'opacity-0':'' }" ></span>
        <span class="block absolute w-6 h-0.5 rounded-sm bg-black duration-500 { menu_open ? 'transform rotate-45':'' }"></span>
        <span class="block absolute w-6 h-0.5 rounded-sm bg-black duration-500 { menu_open ? 'transform -rotate-45':'' }"></span>
        <span class="block absolute w-6 h-0.5 rounded-sm bg-black bottom-2.5 duration-500 { menu_open ? 'opacity-0':'' }"></span>
      </button>
    </div>




    <div class="w-screen container mx-auto sm:flex sm:items-center sm:justify-between">
      <div class=" md:mx-10 m-0  font-medium w-fit p-0 rounded-md flex items-center justify-center">
       
        <img src="/img/logo.svg" alt="logo" class=" {scrolled?'h-12':'h-16'}">
      </div>

      <nav>
        <ul class="sm:flex md:text-xs gap-2 w-full" style="font-family: Poppins, Arial, Helvetica, sans-serif;">
         
          <li on:click="{()=> menu_open = !menu_open }"  class="w-fit px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100" >
            <a href="/" class=" md:text-[#567763] p-1 font-bold text-white hover:text-black font-data uppercase">Home</a>
          </li>
          
          <li on:click="{()=> menu_open = !menu_open }"  class="w-fit px-5 py-2 transform  transition duration-500 hover:scale-100">
					<a href="https://forms.zohopublic.com/keralastartupmission/form/ConstructionInnovationHub/formperma/8Fk9GeVnaCuv78xHePjjzhVD_59yFvxIylusBUFjjyE" target="_blank" class=" bg-blue-900 text-white px-3 py-2  font-semibold cursor-pointer" style="font-family: Poppins, Arial, Helvetica, sans-serif;" >Apply for CIH</a>

          </li>
           

        
        </ul>
      </nav>
    </div>

</div>

<main class="w-full fixed bg-white z-40" >
  <div class="flex sm:hidden" >        
    <img src="/img/logo.svg" alt="Logo" class="p-1 object-contain h-12 px-2">
    <button on:click="{()=> menu_open = !menu_open }" class="z-50 cursor-pointer fixed right-5 w-10 h-10 text-xl ml-auto transition duration-150 hover:shadow leading-none px-2 py-1 border border-solid border-transparent rounded bg-transparent block lg:hidden outline-none focus:outline-none" type="button">
      <span class="block absolute w-6 h-0.5 rounded-sm bg-black top-3 duration-500 { menu_open ? 'opacity-0':'' }" ></span>
      <span class="block absolute w-6 h-0.5 rounded-sm bg-black duration-500 { menu_open ? 'transform rotate-45':'' }"></span>
      <span class="block absolute w-6 h-0.5 rounded-sm bg-black duration-500 { menu_open ? 'transform -rotate-45':'' }"></span>
      <span class="block absolute w-6 h-0.5 rounded-sm bg-black bottom-2.5 duration-500 { menu_open ? 'opacity-0':'' }"></span>
    </button>
  </div>
</main>

