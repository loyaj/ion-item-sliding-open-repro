# ion-item-sliding-open-repro
Reproduction for issue with IonItemSliding in ionicframework (vue)

## Current Behavior
The methods (including `open` and `close`) are not available on the template ref of the `ion-item-sliding` component.
Calling either of these methods (eg. from button handlers) logs an error to the browser's js console rather than having the intended effect (e.g. opening or closing the sliding item).

Furthermore, it appears that the only keys available on the template ref are `disabled`, `ionDrag`, and `routerLink`.

## Expected Behavior
The [ionic documentation for ion-item-sliding](https://ionicframework.com/docs/api/item-sliding#methods)
lists `open` and `close` among the available methods. After binding a template ref to an IonItemSliding component,
calling `open` should programmatically slide the item to expose the sliding item options, and
calling `close` should return the sliding item to the initial state, hiding the options.

I would expect all methods in the documentation to be available, including `open`, `close`, `closeOpened`, `getOpenAmount`, and `getSlidingRatio`.

## Steps to Reproduce
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
