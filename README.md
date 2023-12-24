# code_coverage

# procedure

To ensure comprehensive test coverage, follow the procedure outlined below:

- creating a new test function within the appropriate test suite.
- specify the classes which their coverage increased


## 1-initial code coverage picture

![Coverage Percentages ](https://github.com/ArashST79/code_coverage/blob/main/Screenshot%20(688).png)

## 2-add delete test

```
@Test
	public void testDelete_shouldDeletePersonWithSuccessWhenAllPersonsInfoIsFilled() {
		// Arrange
		String personName = "John";
		Person person = new Person();
		person.setName(personName);

		// Act
		service.delete(personName);

		// Assert
		verify(repository, times(1)).delete(eq(personName));
	}
```


![Coverage Percentages ](https://github.com/ArashST79/code_coverage/blob/main/Screenshot%20(689).png)

### changes
- PersonValidator methods from 75% to 100%
- PersonServiceImpl methods from 40% to 60%

## 3-cross the cross walk

```
@Test
	public void testFootpassengerCrossTheStreet_isSafeWhenCrossTheCrossWalk() {

		Traffic currentTrafic = new Traffic();
		currentTrafic.setIntenseCarTraffic(true);
		Footpassenger currentFootpassengerBehavior = new Footpassenger();
		currentFootpassengerBehavior.setCrossedTheCrosswalk((true));
		currentFootpassengerBehavior.setCrossedTheRoad(true);
		currentFootpassengerBehavior.setCrossedTrafficLigth(TrafficLigth.GREEN);

		Assertions.assertThatThrownBy(() -> trafficBehaviorService.footpassengerCrossTheStreet(currentTrafic, currentFootpassengerBehavior))
				.isInstanceOf(BehaviorException.class)
				.hasMessageContaining("You are safe, but still be careful");
	}

```


![Coverage Percentages ](https://github.com/ArashST79/code_coverage/blob/main/Screenshot%20(690).png)

### changes
- FootPassenger methods from 80% to 100%

## 3-cross the 2way street

```
@Test
	public void testFootpassengerCrossThe2wayStreet_shouldThrowBehaviorExceptionWhenFootpassengerDontlookBothWays() {

		Traffic currentTrafic = new Traffic();
		currentTrafic.setIntenseCarTraffic(true);
		currentTrafic.setStreetDirectionFlow(StreetDirectionFlow.TWO_WAY);
		Footpassenger currentFootpassengerBehavior = new Footpassenger();
		currentFootpassengerBehavior.setCrossedTheRoad(true);
		currentFootpassengerBehavior.setCrossedTrafficLigth(TrafficLigth.GREEN);
		currentFootpassengerBehavior.setLookedToTheLeft(true);
		currentFootpassengerBehavior.setLookedToTheRight(false);

		Assertions.assertThatThrownBy(() -> trafficBehaviorService.footpassengerCrossTheStreet(currentTrafic, currentFootpassengerBehavior))
				.isInstanceOf(BehaviorException.class)
				.hasMessage("You should look both ways");

	}

```


![Coverage Percentages ](https://github.com/ArashST79/code_coverage/blob/main/Screenshot%20(691).png)

### changes
- Traffic methods from 20% to 40%
- StreetDirectionFlow methods and class from 0% to 100%
