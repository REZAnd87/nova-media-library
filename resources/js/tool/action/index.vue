<template>
  <div class="flex flex-wrap mb-4 select-none">

    <checkbox-with-label
      class="cursor-pointer mr-4"
      v-if="!$parent.field || $parent.isArray"
      @input="changeBulk"
    >{{ __('Bulk Select') }}</checkbox-with-label>

    <button class="
    mr-4
flex-shrink-0 shadow rounded focus:outline-none ring-sky-200 dark:ring-gray-600 focus:ring bg-sky-500 hover:bg-sky-400
active:bg-sky-600 text-white dark:text-gray-800 inline-flex items-center font-bold px-4 h-9 text-sm flex-shrink-0"
            type="button"
            @click="bulkAll"
            v-if="$parent.bulk.enable"
    >{{ __('Select All') }}</button>

    <template v-if="$parent.bulkLen()">
      <button class="
    mr-4
flex-shrink-0 shadow rounded focus:outline-none ring-red-200 dark:ring-gray-600 focus:ring bg-red-500 hover:bg-red-400
active:bg-red-600 text-white dark:text-gray-800 inline-flex items-center font-bold px-4 h-9 text-sm flex-shrink-0"
              type="button"
              @click="$parent.deleteFiles(Object.keys($parent.bulk.ids))">
        {{ __('Delete') }} ({{ $parent.bulkLen() }})
      </button>

      <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-1 px-2 rounded bg-success cursor-pointer shadow-md max-w-full mr-4"
              v-if="$parent.field && $parent.bulk.enable && $parent.bulkLen()"
              type="button"
              @click="pushFiles">
        {{ __('Choose') }} ({{ $parent.bulkLen() }})
      </button>
    </template>

    <label class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-1 px-2 rounded bg-90 text-center text-xl cursor-pointer shadow-md max-w-full ml-auto">
      <input
        id="nml_upload"
        class="form-file-input"
        type="file"
        multiple
        :accept="$parent.config.accept"
        @change="selectFiles"
      />
      {{ __('Upload') }}
    </label>

  </div>
</template>



<script src="./script.js"></script>
