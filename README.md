<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My To-Do List</title>

    <script src="https://cdn.tailwindcss.com"></script>

    <script>
        tailwind.config = {
            darkMode: 'class'
        }
    </script>
</head>

<body class="bg-gradient-to-br from-blue-100 via-purple-100 to-pink-100
             dark:bg-gray-900 min-h-screen flex items-center justify-center p-4">

    <div class="w-full max-w-2xl bg-white dark:bg-gray-800 rounded-3xl
                shadow-2xl p-6">

        <!-- Header -->
        <div class="flex justify-between items-center mb-6">

            <div>
                <h1 class="text-3xl font-bold text-gray-800 dark:text-white">
                    📝 My To-Do List
                </h1>

                <p class="text-gray-500 dark:text-gray-400">
                    Organize your day, stay productive!
                </p>
            </div>

            <!-- Dark Mode -->
            <button onclick="toggleDarkMode()"
                class="text-2xl bg-gray-100 dark:bg-gray-700
                       p-3 rounded-full">
                🌙
            </button>
        </div>


        <!-- Add Task -->
        <div class="bg-gray-50 dark:bg-gray-700 p-4 rounded-2xl mb-5">

            <input
                id="taskInput"
                type="text"
                placeholder="What do you need to do?"
                class="w-full p-3 rounded-xl border mb-3
                       dark:bg-gray-800 dark:text-white
                       focus:outline-none focus:ring-2 focus:ring-blue-500">

            <div class="flex gap-2">

                <select id="priority"
                    class="flex-1 p-3 rounded-xl border
                           dark:bg-gray-800 dark:text-white">

                    <option value="Low">🟢 Low Priority</option>
                    <option value="Medium">🟡 Medium Priority</option>
                    <option value="High">🔴 High Priority</option>

                </select>

                <input id="dueDate"
                    type="date"
                    class="flex-1 p-3 rounded-xl border
                           dark:bg-gray-800 dark:text-white">

                <button onclick="addTask()"
                    class="bg-blue-600 hover:bg-blue-700
                           text-white px-5 rounded-xl font-bold">
                    + Add
                </button>

            </div>
        </div>


        <!-- Search -->
        <input
            id="searchInput"
            onkeyup="displayTasks()"
            type="text"
            placeholder="🔍 Search tasks..."
            class="w-full p-3 rounded-xl border mb-4
                   dark:bg-gray-700 dark:text-white">


        <!-- Filters -->
        <div class="flex flex-wrap gap-2 mb-5">

            <button onclick="setFilter('all')"
                class="filterBtn bg-blue-600 text-white px-4 py-2 rounded-lg">
                All
            </button>

            <button onclick="setFilter('active')"
                class="filterBtn bg-gray-200 px-4 py-2 rounded-lg">
                Active
            </button>

            <button onclick="setFilter('completed')"
                class="filterBtn bg-gray-200 px-4 py-2 rounded-lg">
                Completed
            </button>

            <button onclick="clearCompleted()"
                class="bg-red-500 text-white px-4 py-2 rounded-lg">
                Clear Completed
            </button>

        </div>


        <!-- Task List -->
        <div id="taskList" class="space-y-3"></div>


        <!-- Statistics -->
        <div class="mt-6 grid grid-cols-3 gap-3 text-center">

            <div class="bg-blue-100 p-3 rounded-xl">
                <p class="text-2xl font-bold text-blue-600" id="totalCount">
                    0
                </p>
                <p class="text-sm">Total</p>
            </div>

            <div class="bg
