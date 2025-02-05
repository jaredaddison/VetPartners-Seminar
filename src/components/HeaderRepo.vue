<template>
  <Popover open="true" class="relative bg-white">
    <div
      class="absolute inset-0 shadow z-30 pointer-events-none"
      aria-hidden="true"
    />
    <div class="relative z-20">
      <div
        class="
          max-w-7xl
          mx-auto
          flex
          justify-between
          items-center
          px-4
          py-5
          sm:px-6
          sm:py-4
          lg:px-8
          md:justify-start
          md:space-x-10
        "
      >
        <div class="-mr-2 -my-2 md:hidden">
          <PopoverButton
            class="
              bg-white
              rounded-md
              p-2
              inline-flex
              items-center
              justify-center
              text-gray-400
              hover:text-gray-500
              hover:bg-gray-100
              focus:outline-none
              focus:ring-2 focus:ring-inset focus:ring-vetpartners
            "
          >
            <span class="sr-only">Open menu</span>
            <MenuIcon class="h-6 w-6" aria-hidden="true" />
          </PopoverButton>
        </div>
        <div
          class="hidden md:flex-1 md:flex md:items-center md:justify-between"
        >
          <PopoverGroup as="nav" class="flex space-x-10">
            <Popover v-slot="{ open }">
              <PopoverButton
                :class="[
                  open ? 'text-gray-900' : 'text-gray-500',
                  'group bg-white rounded-md inline-flex items-center text-base font-medium hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-vetpartners',
                ]"
              >
                <img
                  src="https://vet.partners/wp-content/uploads/2018/11/logo.png"
                  alt="Veterinary Portal"
                />
                <ChevronDownIcon
                  :class="[
                    open ? 'text-gray-600' : 'text-gray-400',
                    'ml-2 h-5 w-5 group-hover:text-gray-500',
                  ]"
                  aria-hidden="true"
                />
              </PopoverButton>

              <transition
                enter-active-class="transition ease-out duration-200"
                enter-from-class="opacity-0 -translate-y-1"
                enter-to-class="opacity-100 translate-y-0"
                leave-active-class="transition ease-in duration-150"
                leave-from-class="opacity-100 translate-y-0"
                leave-to-class="opacity-0 -translate-y-1"
              >
                <PopoverPanel
                  class="
                    hidden
                    md:block
                    absolute
                    z-10
                    top-full
                    inset-x-0
                    transform
                    shadow-lg
                    bg-white
                  "
                >
                  <div
                    class="
                      max-w-7xl
                      mx-auto
                      grid
                      gap-y-6
                      px-4
                      py-6
                      sm:grid-cols-2
                      sm:gap-8
                      sm:px-6
                      sm:py-8
                      lg:grid-cols-4
                      lg:px-8
                      lg:py-12
                      xl:py-16
                    "
                  >
                    <a
                      v-for="item in solutions"
                      :key="item.name"
                      :href="item.href"
                      class="
                        -m-3
                        p-3
                        flex flex-col
                        justify-between
                        rounded-lg
                        hover:bg-gray-50
                      "
                    >
                      <div class="flex md:h-full lg:flex-col">
                        <div class="flex-shrink-0">
                          <span
                            class="
                              inline-flex
                              items-center
                              justify-center
                              h-10
                              w-10
                              rounded-md
                              bg-vetpartners
                              text-white
                              sm:h-12
                              sm:w-12
                            "
                          >
                            <component
                              :is="item.icon"
                              class="h-6 w-6"
                              aria-hidden="true"
                            />
                          </span>
                        </div>
                        <div
                          class="
                            ml-4
                            md:flex-1 md:flex md:flex-col
                            md:justify-between
                            lg:ml-0
                            lg:mt-4
                          "
                        >
                          <div>
                            <p class="text-base font-medium text-gray-900">
                              {{ item.name }}
                            </p>
                            <p class="mt-1 text-sm text-gray-500">
                              {{ item.description }}
                            </p>
                          </div>
                          <p
                            class="
                              mt-2
                              text-sm
                              font-medium
                              text-vetpartners
                              lg:mt-4
                            "
                          >
                            Learn more <span aria-hidden="true">&rarr;</span>
                          </p>
                        </div>
                      </div>
                    </a>
                  </div>
                  <div class="bg-gray-50">
                    <div
                      class="
                        max-w-7xl
                        mx-auto
                        space-y-6
                        px-4
                        py-5
                        sm:flex
                        sm:space-y-0 sm:space-x-10
                        sm:px-6
                        lg:px-8
                      "
                    >
                      <div
                        v-for="item in callsToAction"
                        :key="item.name"
                        class="flow-root"
                      >
                        <a
                          :href="item.href"
                          class="
                            -m-3
                            p-3
                            flex
                            items-center
                            rounded-md
                            text-base
                            font-medium
                            text-gray-900
                            hover:bg-gray-100
                          "
                        >
                          <component
                            :is="item.icon"
                            class="flex-shrink-0 h-6 w-6 text-gray-400"
                            aria-hidden="true"
                          />
                          <span class="ml-3">{{ item.name }}</span>
                        </a>
                      </div>
                    </div>
                  </div>
                </PopoverPanel>
              </transition>
            </Popover>
          </PopoverGroup>
          <div class="flex items-center md:ml-12">
            <a
              href="#"
              class="text-base font-medium text-gray-500 hover:text-gray-900"
            >
              Sign in
            </a>
            <a
              href="#"
              class="
                ml-8
                inline-flex
                items-center
                justify-center
                px-4
                py-2
                border border-transparent
                rounded-md
                shadow-sm
                text-base
                font-medium
                text-white
                bg-vetpartners
                hover:bg-indigo-700
              "
            >
              Sign up
            </a>
          </div>
        </div>
      </div>
    </div>

    <transition
      enter-active-class="duration-200 ease-out"
      enter-from-class="opacity-0 scale-95"
      enter-to-class="opacity-100 scale-100"
      leave-active-class="duration-100 ease-in"
      leave-from-class="opacity-100 scale-100"
      leave-to-class="opacity-0 scale-95"
    >
      <PopoverPanel
        focus
        class="
          absolute
          z-30
          top-0
          inset-x-0
          p-2
          transition
          transform
          origin-top-right
          md:hidden
        "
      >
        <div
          class="
            rounded-lg
            shadow-lg
            ring-1 ring-black ring-opacity-5
            bg-white
            divide-y-2 divide-gray-50
          "
        >
          <div class="pt-5 pb-6 px-5 sm:pb-8">
            <div class="flex items-center justify-between">
              <div>
                <img
                  class="h-8 w-auto"
                  src="https://tailwindui.com/img/logos/workflow-mark-vetpartners.svg"
                  alt="Workflow"
                />
              </div>
              <div class="-mr-2">
                <PopoverButton
                  class="
                    bg-white
                    rounded-md
                    p-2
                    inline-flex
                    items-center
                    justify-center
                    text-gray-400
                    hover:text-gray-500
                    hover:bg-gray-100
                    focus:outline-none
                    focus:ring-2 focus:ring-inset focus:ring-vetpartners
                  "
                >
                  <span class="sr-only">Close menu</span>
                  <XIcon class="h-6 w-6" aria-hidden="true" />
                </PopoverButton>
              </div>
            </div>
            <div class="mt-6 sm:mt-8">
              <nav>
                <div class="grid gap-7 sm:grid-cols-2 sm:gap-y-8 sm:gap-x-4">
                  <a
                    v-for="item in solutions"
                    :key="item.name"
                    :href="item.href"
                    class="
                      -m-3
                      flex
                      items-center
                      p-3
                      rounded-lg
                      hover:bg-gray-50
                    "
                  >
                    <div
                      class="
                        flex-shrink-0 flex
                        items-center
                        justify-center
                        h-10
                        w-10
                        rounded-md
                        bg-vetpartners
                        text-white
                        sm:h-12
                        sm:w-12
                      "
                    >
                      <component
                        :is="item.icon"
                        class="h-6 w-6"
                        aria-hidden="true"
                      />
                    </div>
                    <div class="ml-4 text-base font-medium text-gray-900">
                      {{ item.name }}
                    </div>
                  </a>
                </div>
                <div class="mt-8 text-base">
                  <a
                    href="#"
                    class="font-medium text-vetpartners hover:text-vetpartners"
                  >
                    View all products <span aria-hidden="true">&rarr;</span></a
                  >
                </div>
              </nav>
            </div>
          </div>
          <div class="py-6 px-5">
            <div class="grid grid-cols-2 gap-4">
              <a
                href="#"
                class="
                  rounded-md
                  text-base
                  font-medium
                  text-gray-900
                  hover:text-gray-700
                "
              >
                Pricing
              </a>

              <a
                href="#"
                class="
                  rounded-md
                  text-base
                  font-medium
                  text-gray-900
                  hover:text-gray-700
                "
              >
                Docs
              </a>

              <a
                href="#"
                class="
                  rounded-md
                  text-base
                  font-medium
                  text-gray-900
                  hover:text-gray-700
                "
              >
                Company
              </a>

              <a
                href="#"
                class="
                  rounded-md
                  text-base
                  font-medium
                  text-gray-900
                  hover:text-gray-700
                "
              >
                Resources
              </a>

              <a
                href="#"
                class="
                  rounded-md
                  text-base
                  font-medium
                  text-gray-900
                  hover:text-gray-700
                "
              >
                Blog
              </a>

              <a
                href="#"
                class="
                  rounded-md
                  text-base
                  font-medium
                  text-gray-900
                  hover:text-gray-700
                "
              >
                Contact Sales
              </a>
            </div>
            <div class="mt-6">
              <a
                href="#"
                class="
                  w-full
                  flex
                  items-center
                  justify-center
                  px-4
                  py-2
                  border border-transparent
                  rounded-md
                  shadow-sm
                  text-base
                  font-medium
                  text-white
                  bg-vetpartners
                  hover:bg-indigo-700
                "
              >
                Sign up
              </a>
              <p class="mt-6 text-center text-base font-medium text-gray-500">
                Existing customer?
                {{ ' ' }}
                <a href="#" class="text-vetpartners hover:text-vetpartners">
                  Sign in
                </a>
              </p>
            </div>
          </div>
        </div>
      </PopoverPanel>
    </transition>
  </Popover>
</template>

<script setup>
import {
  Popover,
  PopoverButton,
  PopoverGroup,
  PopoverPanel,
} from '@headlessui/vue'
import {
  BookmarkAltIcon,
  BriefcaseIcon,
  ChartBarIcon,
  CheckCircleIcon,
  CursorClickIcon,
  DesktopComputerIcon,
  GlobeAltIcon,
  InformationCircleIcon,
  MenuIcon,
  NewspaperIcon,
  OfficeBuildingIcon,
  PhoneIcon,
  PlayIcon,
  ShieldCheckIcon,
  UserGroupIcon,
  ViewGridIcon,
  XIcon,
} from '@heroicons/vue/outline'
import { ChevronDownIcon } from '@heroicons/vue/solid'

const solutions = [
  {
    name: 'Trauma Triage Score',
    description:
      'How sick is your patient? Do more than guess, put a number on it!',
    href: '#',
    icon: ChartBarIcon,
  },
  {
    name: 'Nursing Resources',
    description: 'Take home the best nursing resources for your team',
    href: '#',
    icon: CursorClickIcon,
  },
  {
    name: 'Protection',
    description: 'Learn the skills to protect your team from panick',
    href: '#',
    icon: ShieldCheckIcon,
  },
  {
    name: 'Advanced Anaesthesia',
    description: 'Want to save a life? Stop it from dying int he first place.',
    href: '#',
    icon: ViewGridIcon,
  },
]
</script>
