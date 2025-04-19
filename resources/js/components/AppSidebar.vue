<script setup lang="ts">
import { usePage } from '@inertiajs/vue3';
import { computed } from 'vue';

import NavFooter from '@/components/NavFooter.vue';
import NavMain from '@/components/NavMain.vue';
import NavUser from '@/components/NavUser.vue';
import NavBloodDrives from '@/components/NavBloodDrives.vue';

import {
  Sidebar,
  SidebarContent,
  SidebarFooter,
  SidebarHeader,
  SidebarMenu,
  SidebarMenuButton,
  SidebarMenuItem,
} from '@/components/ui/sidebar';

import { type NavItem, type SharedData } from '@/types';
import { Link } from '@inertiajs/vue3';
import { BookOpen, Folder, LayoutGrid, CalendarClock, Users, ClipboardList, Droplets, Ambulance } from 'lucide-vue-next';
import AppLogo from './AppLogo.vue';

const mainNavItems: NavItem[] = [
    { 
        title: 'Dashboard', 
        href: '/dashboard', 
        icon: LayoutGrid 
    }, 
    { 
        title: 'Users', 
        href: '/settings', 
        icon: Users
    },
    { 
        title: 'Inventory', 
        href: '/inventory', 
        icon: ClipboardList 
    },
    { 
        title: 'Blood Request', 
        href: '/blood-request', 
        icon: Droplets 
    },
    { 
        title: 'Blood Drives', 
        href: '/blood-drives', 
        icon: Ambulance 
    },
];

const bloodDriveNavItems: NavItem[] = [
    { 
        title: 'Central Mindanao University', 
        href: '/test', 
        icon: CalendarClock 
    },
];

const footerNavItems: NavItem[] = [
    {
        title: 'Github',
        href: 'https://github.com/Delakzz/lifeline_connect',
        icon: Folder,
    },
//   {
//     title: 'Documentation',
//     href: 'https://laravel.com/docs/starter-kits',
//     icon: BookOpen,
//   },
];

const page = usePage<SharedData>();
const currentUrl = computed(() => page.url);
</script>

<template>
    <Sidebar collapsible="icon" variant="inset">
        <SidebarHeader>
            <SidebarMenu>
                <SidebarMenuItem>
                    <SidebarMenuButton size="lg" as-child>
                        <Link :href="route('dashboard')">
                            <AppLogo />
                        </Link>
                    </SidebarMenuButton>
                </SidebarMenuItem>
            </SidebarMenu>
        </SidebarHeader>

        <SidebarContent>
             <SidebarContent>
                <NavMain :items="mainNavItems" :current-url="currentUrl" />
                <NavBloodDrives :items="bloodDriveNavItems" :current-url="currentUrl" />
            </SidebarContent>
        </SidebarContent>

        <SidebarFooter>
            <NavFooter :items="footerNavItems" />
            <NavUser />
        </SidebarFooter>
    </Sidebar>
    <slot />
</template>
