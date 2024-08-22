### What Not to Test
- Configuration settings
- Route declarations
- Internal router functionality

### What to test
- Instead of testing the router, we are testing that we configured the router correctly and that navigation events are initiating the correct views, in the correct places, in the correct state.

### End-to-End Test
- Perfect for testing route changes
- Verify that route links to the correct views
- Verify that routes verify correctly and pass the correct state.

### RouterTestingHarness
- Prior to Angular 15, testing router links was notoriously difficult.
- Since 15, Angular has introduced the `RouterTestingHarness` to solve this problem.