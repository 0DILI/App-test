<template>
  <div class="bg-[#D3D3D3] flex flex-col justify-center items-center h-screen px-2 py-7">
    <div class="bg-white w-full max-w-[800px] mx-auto p-4 rounded-lg flow">
      <span class="flex items-center justify-between">
        <img src="./assets/arrow1.svg" />
        <p class="text-[20px] font-bold">Shareable Triggers</p>
      </span>

      <div class="mt-10">
        <div>
          <p class="text-[18px] font-semibold">Name your trigger entry</p>
          <input
            type="text"
            placeholder="What would you like to name this Trigger entry"
            class="w-full mt-5 bg-[#F7F7F7] border border-[rgba(0,0,0,0.02)] p-4 rounded-[8px] outline-none focus:ring-0 focus:outline-none"
          />
        </div>

        <div class="mt-8">
          <p class="text-[18px] font-semibold">Describe your child’s Trigger</p>
          <div class="relative w-full p-4 bg-[#F7F7F7] rounded-xl mt-5">
            <textarea
              placeholder="Type the trigger description or use the audio feature"
              class="w-full h-32 p-2 pr-12 bg-transparent border-none resize-none focus:outline-none focus:ring-0 placeholder-gray-500"
            ></textarea>

            <!-- Mic button -->
            <button
              class="absolute bottom-4 right-4 flex items-center justify-center w-10 h-10 rounded-full bg-black text-white"
            >
              <!-- Mic icon (Heroicons example) -->
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                class="w-5 h-5"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M12 1a3 3 0 00-3 3v7a3 3 0 006 0V4a3 3 0 00-3-3zm-7 9a7 7 0 0014 0m-7 7v6m-4 0h8"
                />
              </svg>
            </button>
          </div>
        </div>

        <div class="mt-8">
          <p class="text-[18px] font-semibold">
            What category does the indicated trigger belong to?
          </p>
          <!-- Horizontal Scrollable Buttons -->
          <div
            class="flex overflow-x-auto whitespace-nowrap mt-4 space-x-4 px-2 scrollbar-hide w-full"
          >
            <button class="px-6 py-2 rounded-full bg-black text-white flex-shrink-0">
              Sensory
            </button>
            <button class="px-6 py-2 rounded-full bg-gray-200 text-gray-700 flex-shrink-0">
              Emotional
            </button>
            <button class="px-6 py-2 rounded-full bg-gray-200 text-gray-700 flex-shrink-0">
              Environmental
            </button>
            <button class="px-6 py-2 rounded-full bg-gray-200 text-gray-700 flex-shrink-0">
              Social
            </button>
            <button class="px-6 py-2 rounded-full bg-gray-200 text-gray-700 flex-shrink-0">
              Academic
            </button>
            <button class="px-6 py-2 rounded-full bg-gray-200 text-gray-700 flex-shrink-0">
              Another
            </button>
            <button class="px-6 py-2 rounded-full bg-gray-200 text-gray-700 flex-shrink-0">
              Another
            </button>
            <button class="px-6 py-2 rounded-full bg-gray-200 text-gray-700 flex-shrink-0">
              Social22
            </button>
          </div>

          <textarea
            placeholder="eg: loud noises, bright lights, strong smells, certain textures, food sensitivities"
            class="w-full h-32 p-2 pr-12 p-4 bg-[#F7F7F7] rounded-xl mt-5 border-none resize-none focus:outline-none focus:ring-0 placeholder-gray-500"
          ></textarea>
        </div>

        <div class="mt-10">
          <p class="text-[18px] font-semibold">Choose Intensity Level</p>
          <!-- <img src="./assets/img1.svg" alt="" /> -->

          <div class="flex items-center mt-3">
            <div class="w-full max-w-md pl-2 space-y-12">
              <!-- The main container for the slider -->
              <div
                ref="sliderContainer"
                class="relative w-full select-none pt-4"
                @mousedown="handleDragStart"
                @touchstart="handleDragStart"
                @click="handleClick"
              >
                <!-- Slider Track with Gradient -->
                <div
                  class="h-1.5 w-full rounded-full bg-gradient-to-r from-green-400 via-yellow-400 to-red-500"
                ></div>

                <!-- Snap Point Dots -->
                <div class="absolute top-[14px] w-full -translate-y-1/2">
                  <div
                    v-for="(level, index) in levels"
                    :key="`dot-${level}`"
                    class="absolute w-4 h-4 -translate-x-1/2 bg-gray-700 rounded-full"
                    :style="{ left: `${index * 25}%` }"
                  ></div>
                </div>

                <!-- Draggable Thumb and Indicator Line -->
                <div
                  class="absolute top-[14px] -translate-y-1/2 cursor-grab active:cursor-grabbing transition-all duration-300 ease-out"
                  :style="{ left: thumbPosition }"
                >
                  <!-- The vertical line connecting thumb to dot -->
                  <div class="absolute bottom-2 left-1/2 w-0.5 h-6 bg-gray-800"></div>
                  <!-- The draggable thumb itself -->
                  <div
                    class="w-6 h-6 bg-white border-2 border-gray-800 rounded-full shadow-lg"
                  ></div>
                </div>

                <!-- Difficulty Labels -->
                <div class="mt-8 flex justify-between text-base font-medium text-gray-800">
                  <span v-for="level in levels" :key="level" class="w-1/5 text-center">
                    {{ level }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="mt-10">
          <p class="text-[18px] font-semibold">What are some Early Signs?</p>

          <span class="flex items-center justify-between bg-[#F7F7F7] rounded-[8px] p-5 mt-5">
            <p class="text-[14px] font-medium" style="color: #000; opacity: 0.7">
              Sweaty Neck with Itchy Nose
            </p>
            <img src="./assets/edit.svg" alt="" />
          </span>

          <input
            type="text"
            placeholder="What would you like to name this Trigger entry"
            class="w-full mt-5 border border-[#DEDEDE] p-4 rounded-[8px] outline-none focus:ring-0 focus:outline-none"
          />

          <button class="flex items-center gap-3 bg-black p-3 rounded-[12px] mt-4">
            <img src="./assets/plus.svg" />
            <p class="text-[12px] text-white font-medium">Add List</p>
          </button>
        </div>

        <div class="mt-10">
          <p class="text-[18px] font-semibold">Attachments</p>

          <p class="text-[14px] font-medium" style="opacity: 0.5">
            Record of behavioral outcomes (e.g., meltdown, shutdown, avoidance)
          </p>

          <div class="w-full mt-6">
            <!-- The dashed border container -->
            <div
              class="flex items-center justify-center w-full h-64 bg-gray-50 border-2 border-dashed border-gray-300 rounded-xl hover:bg-gray-100 transition-colors duration-300 cursor-pointer"
            >
              <!-- SVG Camera Icon -->
              <div class="text-center">
                <img src="./assets/camera.svg" class="mx-auto" />
                <p class="mt-2 text-sm text-gray-500">Click to upload or drag and drop</p>
                <p class="text-xs text-gray-400">SVG, PNG, JPG or GIF (MAX. 800x400px)</p>
              </div>
            </div>
          </div>
        </div>

        <div class="mt-10">
          <p class="text-[18px] font-semibold">Notess</p>
          <input
            type="text"
            placeholder="Type things to be noted"
            class="w-full mt-5 bg-[#F7F7F7] border border-[rgba(0,0,0,0.02)] p-4 rounded-[8px] outline-none focus:ring-0 focus:outline-none"
          />

          <span class="flex">
            <button class="bg-black p-3 rounded-[8px] mt-4">
              <p class="text-[18px] font-semibold text-white font-medium">Save</p>
            </button>

            <button class="bg-black p-3 rounded-[8px] mt-4 border border-[#DEDEDE]">
              <p class="text-[18px] font-semibold text-white font-medium">Add to Drafts</p>
            </button>
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

// --- State ---

// Updated array to match the 5 levels from the image.
const levels = ['Easy', 'Mild', 'Hard', 'Tough', 'Special']

// A ref to hold the index of the currently selected level (0-4).
const selectedIndex = ref(2) // Default to 'Hard'

// A ref to track whether the user is currently dragging the thumb.
const isDragging = ref(false)

// A ref to bind to the slider's main container element in the template.
const sliderContainer = ref(null)

// --- Computed Properties ---

// Computes the percentage position for the thumb based on the selected index.
// For 5 items, the positions are 0%, 25%, 50%, 75%, and 100%.
const positionPercentage = computed(() => {
  if (levels.length <= 1) return '0%'
  return `${(selectedIndex.value / (levels.length - 1)) * 100}%`
})

// Computes the `left` CSS property for the thumb.
// It subtracts half the thumb's width (12px) to center it on the snap points.
const thumbPosition = computed(() => `calc(${positionPercentage.value} - 12px)`)

// --- Methods ---

/**
 * Updates the selectedIndex based on the horizontal position (x-coordinate)
 * of a mouse or touch event within the slider container.
 * @param {number} clientX - The clientX from the mouse/touch event.
 */
const updateSelection = (clientX) => {
  if (!sliderContainer.value) return

  const rect = sliderContainer.value.getBoundingClientRect()
  const position = Math.max(0, Math.min(rect.width, clientX - rect.left))
  const percentage = position / rect.width

  // Determine the closest snap point index based on the percentage.
  const closestIndex = Math.round(percentage * (levels.length - 1))
  selectedIndex.value = closestIndex
}

/**
 * Handles the initial click on the slider to directly set the level.
 * @param {MouseEvent} event
 */
const handleClick = (event) => {
  updateSelection(event.clientX)
}

/**
 * Initiates the dragging process on mousedown or touchstart.
 * @param {MouseEvent | TouchEvent} event
 */
const handleDragStart = (event) => {
  isDragging.value = true
  const clientX = event.type === 'touchstart' ? event.touches[0].clientX : event.clientX
  updateSelection(clientX)
}

/**
 * Handles the dragging movement, updating the selection in real-time.
 * @param {MouseEvent | TouchEvent} event
 */
const handleDragMove = (event) => {
  if (!isDragging.value) return
  event.preventDefault()
  const clientX = event.type === 'touchmove' ? event.touches[0].clientX : event.clientX
  updateSelection(clientX)
}

/**
 * Ends the dragging process on mouseup or touchend.
 */
const handleDragEnd = () => {
  isDragging.value = false
}

// --- Lifecycle Hooks ---

onMounted(() => {
  window.addEventListener('mousemove', handleDragMove)
  window.addEventListener('touchmove', handleDragMove, { passive: false })
  window.addEventListener('mouseup', handleDragEnd)
  window.addEventListener('touchend', handleDragEnd)
})

onUnmounted(() => {
  window.removeEventListener('mousemove', handleDragMove)
  window.removeEventListener('touchmove', handleDragMove)
  window.removeEventListener('mouseup', handleDragEnd)
  window.removeEventListener('touchend', handleDragEnd)
})
</script>

<style scoped>
.flow {
  overflow-y: scroll;
  /* height: 500; */
}
</style>
