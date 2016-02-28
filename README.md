# ProblemSet06JamesAndrus
##Class to test Merge sorts with a randomly shuffled array

```
public class MergeTestRandomShufflePS06 {
	public static void main(String[] args) {
		Integer[] ints = new Integer[10000000];
		// fill array with integers
		for (int i = 0; i < ints.length; i++) {
			ints[i] = i + 1;
		}
		int counter = 0;
		double averageTime = 0;
		// while loop to repeat experiment
		while (counter < 10) {
			// shuffle
			Knuth.shuffle(ints);
			//start timer
			Stopwatch timer = new Stopwatch();
			// sort
			// MergeA.sort(ints);
			// MergeB.sort(ints);
			// MergeC.sort(ints);
			// MergeAB.sort(ints);
			// MergeAC.sort(ints);
			// MergeBC.sort(ints);
			// MergeX.sort(ints);
			Merge.sort(ints);
			averageTime += timer.elapsedTime();
			counter++;
		}
		System.out.println("Average time elapsed " + averageTime / counter);
	}
}
```
##Class to test Merge sorts with a partially sorted array along with partiallyUnsort() method and swap()
```
public class MergeTestPartiallySortedPS06 {
	public static void main(String[] args) {
		Integer[] ints = new Integer[10000000];
		// fill array with integers
		for (int i = 0; i < ints.length; i++) {
			ints[i] = i + 1;
		}
		int counter = 0;
		double averageTime = 0;
		// while loop to repeat experiment
		while (counter < 10) {
			// partially unsort the array for experiment.
			partiallyUnsort(ints);
			//start timer
			Stopwatch timer = new Stopwatch();
			// sort
			// MergeA.sort(ints);
			// MergeB.sort(ints);
			// MergeC.sort(ints);
			// MergeAB.sort(ints);
			// MergeAC.sort(ints);
			// MergeBC.sort(ints);
			// MergeX.sort(ints);
			Merge.sort(ints);
			System.out.println(timer.elapsedTime());
			averageTime += timer.elapsedTime();
			counter++;
		}
		System.out.println("Average time elapsed " + averageTime / counter);
	}
	private static void partiallyUnsort(Integer[] a) {
		int intervals = 5;
		int index = intervals;
		while (index < a.length) {
			swap(a, index, index + 1);
			index += intervals;
		}
	}
	private static void swap(Comparable[] a, int key1, int key2) {
		Comparable temp = null;
		temp = a[key1];
		a[key1] = a[key2];
		a[key2] = temp;
	}
}
```
##Class to test Merge sorts with an array with duplicate elements along with fill() method 
```
public class MergeTestDuplicateKeysPS06 {
	public static void main(String[] args) {
		Integer[] ints = new Integer[10000000];
		// fill array with integers with specified diversity
		fill(ints, 3);
		int counter = 0;
		double averageTime = 0;
		// while loop to repeat experiment
		while (counter <= 10) {
			// shuffle
			Knuth.shuffle(ints);
			//start timer
			Stopwatch timer = new Stopwatch();
			// sort
			// MergeA.sort(ints);
			// MergeB.sort(ints);
			// MergeC.sort(ints);
			// MergeAB.sort(ints);
			// MergeAC.sort(ints);
			// MergeBC.sort(ints);
			// MergeX.sort(ints);
			MergeX.sort(ints);
			System.out.println(timer.elapsedTime());
			averageTime += timer.elapsedTime();
			counter++;
		}
		System.out.println("Average time elapsed " + averageTime / counter);
	}
	private static void fill(Comparable[] a, int diversity) {
		int multiplier = 1;
		for (int i = 0; i < a.length; i++) {
			if ((int) a.length * multiplier / diversity < i) {
				multiplier++;
			}
			a[i] = 1 * multiplier;
		}
	}
}
```
##Code for Tukey Ninther partition and Median-Of-3
```
//Tukey Ninther
int eps = N/8;
int mid = lo + N/2;
int m1 = median3(a, lo, lo + eps, lo + eps + eps);
int m2 = median3(a, mid - eps, mid, mid + eps);
int m3 = median3(a, hi - eps - eps, hi - eps, hi); 
int ninther = median3(a, m1, m2, m3);
exch(a, ninther, lo);

//Plain Median-Of-3
int m = median3(a, lo, lo + N/2, hi);
exch(a, m, lo);
```
