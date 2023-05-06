# ion-item-sliding-open-repro
Reproduction for issue with IonItemSliding in ionicframework (vue)

## Expected Behavior
The [ionic documentation for ion-item-sliding](https://ionicframework.com/docs/api/item-sliding#methods)
lists `open` and `close` among the available methods. After binding a template ref to an IonItemSliding component,
calling `open` should programmatically slide the item to expose the sliding item options, and
calling `close` should return the sliding item to the initial state, hiding the options.

## Current Behavior
The `open` and `close` methods are not available on the template ref of the IonItemSliding component.
Calling either of these methods in button handlers logs an error to the browser's js console rather than opening or closing the sliding item.

Furthermore, it appears that the only keys available on the template ref are `disabled`, `ionDrag`, and `routerLink`.
I would expect that all the methods in the documentation to be available, including `closeOpened`, `getOpenAmount`, and `getSlidingRatio`.

## Reproduction steps
1. `npm install`
2. `npm run dev`
3. Browse to the URL served by vite
   * The UI consists of a sliding item and two buttons: one for opening the sliding item and one for closing it.
4. Click the "Open sliding item" button
5. Observe that the sliding item does not open.
   * Open the browser developer tools console and notice the error logged there:
     `ionItemSlidingRef.value.open is not a function`
6. Manually slide the item open using your pointing device
7. Click the "Close sliding item" button
8. Observe that the sliding item does not close.
   * In the browser developer tools console, notice the error logged there:
     `ionItemSlidingRef.value.close is not a function`
