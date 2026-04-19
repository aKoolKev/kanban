<script>
    import {Button, Card, Modal, P, Dropdown, Radio, DropdownItem} from 'flowbite-svelte';
    import {EditOutline, ChevronDownOutline} from 'flowbite-svelte-icons'

    let viewTaskModal = $state(false);
    let curStatus = $state("Done");
    let isOpen = $state(false);
    
</script>
<h1 class="uppercase text-3xl font-bold text-center m-5">Kanban</h1>

<!-- Kanban board -->
<div class="border border-red-500 grid grid-cols-5 gap-1">

    <!-- BACKLOG -->
    <div class="border border-black text-center">
        <h1 class="uppercase font-bold text-2xl">Backlog</h1>
        
        <div class="border border-black flex flex-col items-center">
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card> 
        </div>
    </div>

    <!-- SPRINT -->
    <div class="border border-black text-center">
        <h1 class="uppercase font-bold text-2xl">Sprint</h1>
        
        <div class="border border-black flex flex-col items-center">
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
        </div>
    </div>

    <!-- IN PROGRESS -->
    <div class="border border-black text-center">
        <h1 class="uppercase font-bold text-2xl">In Progress</h1>
        
        <div class="border border-black flex flex-col items-center">
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
        </div>
    </div>

    <!-- IN REVIEW -->
    <div class="border border-black text-center">
        <h1 class="uppercase font-bold text-2xl">In Review</h1>
        
        <div class="border border-black flex flex-col items-center">
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
            <Card class='m-2 w-5/6 p-2'>
                <h1 class="font-bold">Task Name</h1>
                <p class="text-gray-600 text-xs">Task description here...</p>
            </Card>
        </div>
    </div> 

    <!-- COMPLETED -->
    <div class="border border-black">
        <h1 class="uppercase font-bold text-2xl text-center">Done</h1>
        
        <div class="border border-black flex flex-col items-center">
            <Card class='m-2 w-8/9 p-2'>
                <h1 class="font-bold">Task Name 1</h1>
                <p class="text-gray-600 text-xs mb-2 text-left py-1 px-1 border border-b">Task description here...</p>
                <Button class="w-fit h-6 ml-auto" pill size='sm' onclick={() => (viewTaskModal = true)}>
                    <EditOutline class="shrink-0 h-5 w-5 p-0 m-0" />
                </Button>
            </Card>
            <Card class='m-2 w-8/9 p-2'>
                <h1 class="font-bold">Task Name 2</h1>
                <p class="text-gray-600 text-xs mb-2 text-left py-1 px-1 border border-b">Task description here...</p>
                <Button class="w-fit h-6 ml-auto" pill size='sm' onclick={() => (viewTaskModal = true)}>
                    <EditOutline class="shrink-0 h-5 w-5 p-0 m-0" />
                </Button>
                <P>Current dropdown state: {isOpen ? "Open" : "Closed"}</P>
            </Card>

            <Modal title="Task #" form bind:open={viewTaskModal} onaction={({ action }) => alert(`Handle "${action}"`)}>

                <div>
                    <P>Current dropdown state: {isOpen ? "Open" : "Closed"}</P>
                    <Button class="w-fit h-6" size='sm' onclick={() => (isOpen = false)}>
                        {curStatus}<ChevronDownOutline class="ms-2 h-6 w-6 text-white dark:text-white" />
                    </Button>

                    <Dropdown simple class="w-44 space-y-3 p-3 text-sm" bind:isOpen >
                        <DropdownItem onclick={() => (isOpen = false)}>
                            <Radio name="In Progress" bind:group={curStatus} value={'In Progress'} class="uppercase">In Progress</Radio>
                        </DropdownItem>
                        <DropdownItem>
                            <Radio name="In Review" bind:group={curStatus} value={'In Review'} class="uppercase">In Review</Radio>
                        </DropdownItem>
                        <DropdownItem>
                            <Radio name="Done" bind:group={curStatus} value={'Done'} class="uppercase">Done</Radio>
                        </DropdownItem>
                    </Dropdown>

                </div>

                <P>
                    The European Union’s General Data Protection Regulation (G.D.P.R.) goes into effect on May 25 and is meant to ensure a common set of data rights in the European Union. It requires organizations to
                    notify users as soon as possible of high-risk data breaches that could personally affect them.
                </P>

                <div class="text-center">
                    <h1>Actions</h1>
                    <Button type="submit" value="success">Edit</Button>
                    <Button type="submit" value="success" color="alternative">Change Status</Button>
                    <Button type="submit" value="decline" color="alternative">Delete</Button>
                </div>
            </Modal>
        </div>



    </div> 
</div>