# Navigation-Drawer-Espresso-Testing

run `connectedAndroidTest` task.

```gralde
$ gradle connectedAndroidTest
```

`NavigationViewActions.navigateTo(menu_id)`

```java
@RunWith(AndroidJUnit4.class)
public class MainActivityTest {

    @Rule
    public IntentsTestRule<MainActivity> activityRule = new IntentsTestRule<>(MainActivity.class);

    @Test
    public void test_navigation_view() throws InterruptedException {
        Thread.sleep(2000);

        onView(withId(R.id.drawer_layout)).perform(DrawerActions.open());
        onView(withId(R.id.nav_view)).perform(NavigationViewActions.navigateTo(R.id.nav_big_button));
        Thread.sleep(1000);

        onView(withId(R.id.drawer_layout)).perform(DrawerActions.open());
        onView(withId(R.id.nav_view)).perform(NavigationViewActions.navigateTo(R.id.nav_send));
        Thread.sleep(1000);

        onView(withId(R.id.drawer_layout)).perform(DrawerActions.open());
        onView(withId(R.id.nav_view)).perform(NavigationViewActions.navigateTo(R.id.nav_sample_fragment));
        Thread.sleep(1000);

        // Testing swipe up
        onView(withId(R.id.drawer_layout)).perform(swipeUp());

    }
}

@Test
    public void test_navigationDrawer_open_closed() {

        // Check drawer is closed
        onView(withId(R.id.drawer_layout)).check(matches(isClosed(Gravity.START)));

        // Check if drawer is open
        onView(withId(R.id.drawer_layout))
                .perform(DrawerActions.open())
                .check(matches(isOpen(Gravity.START)));

    }
```


