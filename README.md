# Vue Unit Test Performance Comparison

This is a performance comparison between test runners testing Vue SFCs.

## Comparison

| Runner        | 10 tests  | 100 tests  | 1000 tests | 10000 tests |
| :------------ |:--------- |:---------  |:---------  |:--------- |
| tape | 1.78s |  2.34s |  5.32s |  49.99s |
| jest | 1.94s |  2.98s |  7.64s |  60.44s |
| mocha-webpack | 2.80s |  3.08s |  6.48s |  55.03s |
| karma-mocha | 4.58s |  7.47s |  15.70s |  64.91s |
| ava | 3.60s |  15.08s |  126.81s |  1251.01s |

## Details

The tests use two SFC. You can see the tests inside the runner directories.

The time is the average of 10 runs.

## Results

Currently tape is the fastest.

AVA is by far the slowest. This is because the [current suggested method](https://github.com/avajs/ava/blob/master/docs/recipes/precompiling-with-webpack.md) does not utilize caching. If caching was added, it would be comparable to Jest.

## Usage

Running the test script will generate a results table in RESULTS.md:

```
npm test
```

**Warning: It takes around 5 minutes to run**

## Contributing

Feel free to add an extra test setup. The aim of this project is to find the best setup out there.

### Add a new setup
* Create directory with a descriptive name, using test template below
* Add `Basic.spec.js` file with 30 tests
* Create a `test` script in your package.json
* Add name of directory to `test_runners` array in `test.sh`
* Run tests from the root by running `npm test`

### Test template
Copy this and change the syntax to match your test runner.
```js
it('renders correct text', () => {
  const wrapper = shallow(Basic)
  expect(wrapper.find('.hello h1').text()).toBe('Welcome to Your Vue.js App')
})
```
