# Date Range Picker (jQuery Plugin)

![Main image](https://raw.githubusercontent.com/frankfajardo/bootstrap-daterangepicker/master/drp1.png)

This jQuery date range picker plugin is a *fork* of the [original Date Range Picker for Bootstrap] by [Dan Grossman]. This version however does not require Bootstrap. Only the demo page uses it for presentation of the options. This plugin, like the [original Date Range Picker for Bootstrap], uses [Moment.js] v.2.10.3, which is included in this repository.

## Variations

This version has a few variations:

- It allows the user to select either the *From* or *To* date first. When the user selects another date, it then decides which is the *From* date, and which is the *To* date.

- It hides the `Apply` and `Cancel` buttons until the user selects `Custom Range`. It makes the UI cleaner IMHO.

  These buttons appear to only be relevant to the custom range option, based on the behaviour of the [original Date Range Picker for Bootstrap], I have hidden them by default. 

- It allows the user to delete entry in the bound input field. This is useful for input where you want to allow the user to not specify a date or date range.

  *Note:* If you are using the callback function, this will return ***null*** on both the `start` and `end` parameters. Also, the callback function now receives a 4th parameter, which is a boolean value indicating if the date range is cleared. So you can check this 4th parameter before using the `start` and `end` parameters:
  ```
  $('#config-demo').daterangepicker(
     options, 
     function(start, end, label, cleared) { 
        if (cleared)
           console.log('Date range is cleared.');
        else
           console.log('New date range selected: ' + start.format('YYYY-MM-DD') + ' to ' + end.format('YYYY-MM-DD') + ' (predefined range: ' + label + ')'); 
     });
  ```

- You can allow your users to clear the date range field via the UI, in two ways:


   - You can add an entry to the date range custom ranges like this: 

   ```
   options.ranges = {
      'Clear Date Range': [null, null],
      ...
   };
   ```
   ![First Option](https://github.com/frankfajardo/bootstrap-daterangepicker/blob/master/drp2.png)
   
   *Or*

   - You can show the new `Clear` button like this:

   ```
   options.showClearBtn = true;
   options.clearClass = 'btn-warning'; 
   ```
   ![Second Option](https://github.com/frankfajardo/bootstrap-daterangepicker/blob/master/drp3.png)

   The difference between the two is that the first option *auto-applies*, much like when you click a pre-defined date range. The second option can work with `autoApply` either being `true` or `false`.
   
   You can try either of these options using the demo page. To use the demo page, you need to download this repo.



## License

This code is made available under the same license as Bootstrap. Moment.js is included in this repository
for convenience. It is available under the [MIT license](http://www.opensource.org/licenses/mit-license.php).


Please also refer to the license for the [original Date Range Picker for Bootstrap].




[original Date Range Picker for Bootstrap]:(http://www.daterangepicker.com/)
[Dan Grossman]:(http://www.dangrossman.info/)
[Moment.js]:(http://momentjs.com)
