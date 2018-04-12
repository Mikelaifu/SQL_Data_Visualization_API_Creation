
# Step 3 - Climate Analysis and Exploration

You are now ready to use Python and SQLAlchemy to do basic climate analysis and data exploration on your new weather station tables. All of the following analysis should be completed using SQLAlchemy ORM queries, Pandas, and Matplotlib.

Create a Jupyter Notebook file called climate_analysis.ipynb and use it to complete your climate analysis and data exporation.

Choose a start date and end date for your trip. Make sure that your vacation range is approximately 3-15 days total.

Use SQLAlchemy create_engine to connect to your sqlite database.

Use SQLAlchemy automap_base() to reflect your tables into classes and save a reference to those classes called Station and Measurement.



```python
import sqlalchemy
from sqlalchemy.ext.automap import automap_base
from sqlalchemy.orm import Session
from sqlalchemy import create_engine, inspect, func
```


```python
engine = create_engine("sqlite:///hawaii.sqlite", echo = False )

```

# Reflection


```python
Base = automap_base()
Base.prepare(engine, reflect= True)
Base.classes.keys()
# Station and Measurement
```




    ['Measurements', 'Station']




```python
session = Session(engine)
```


```python
Measurements = Base.classes.Measurements
    
Station = Base.classes.Station
    
```


```python
session.query(Measurements.date).all()
```




    [('2010-01-01'),
     ('2010-01-02'),
     ('2010-01-03'),
     ('2010-01-04'),
     ('2010-01-07'),
     ('2010-01-08'),
     ('2010-01-09'),
     ('2010-01-10'),
     ('2010-01-11'),
     ('2010-01-12'),
     ('2010-01-14'),
     ('2010-01-15'),
     ('2010-01-16'),
     ('2010-01-17'),
     ('2010-01-18'),
     ('2010-01-19'),
     ('2010-01-20'),
     ('2010-01-21'),
     ('2010-01-22'),
     ('2010-01-23'),
     ('2010-01-24'),
     ('2010-01-25'),
     ('2010-01-26'),
     ('2010-01-27'),
     ('2010-01-28'),
     ('2010-01-31'),
     ('2010-02-01'),
     ('2010-02-04'),
     ('2010-02-05'),
     ('2010-02-06'),
     ('2010-02-07'),
     ('2010-02-08'),
     ('2010-02-09'),
     ('2010-02-11'),
     ('2010-02-12'),
     ('2010-02-13'),
     ('2010-02-14'),
     ('2010-02-15'),
     ('2010-02-16'),
     ('2010-02-17'),
     ('2010-02-20'),
     ('2010-02-21'),
     ('2010-02-22'),
     ('2010-02-23'),
     ('2010-02-24'),
     ('2010-02-25'),
     ('2010-02-26'),
     ('2010-02-28'),
     ('2010-03-01'),
     ('2010-03-02'),
     ('2010-03-03'),
     ('2010-03-04'),
     ('2010-03-05'),
     ('2010-03-06'),
     ('2010-03-07'),
     ('2010-03-08'),
     ('2010-03-09'),
     ('2010-03-12'),
     ('2010-03-13'),
     ('2010-03-14'),
     ('2010-03-15'),
     ('2010-03-17'),
     ('2010-03-18'),
     ('2010-03-21'),
     ('2010-03-22'),
     ('2010-03-23'),
     ('2010-03-24'),
     ('2010-03-27'),
     ('2010-03-28'),
     ('2010-03-29'),
     ('2010-03-30'),
     ('2010-03-31'),
     ('2010-04-01'),
     ('2010-04-02'),
     ('2010-04-03'),
     ('2010-04-04'),
     ('2010-04-05'),
     ('2010-04-06'),
     ('2010-04-08'),
     ('2010-04-09'),
     ('2010-04-10'),
     ('2010-04-11'),
     ('2010-04-12'),
     ('2010-04-13'),
     ('2010-04-15'),
     ('2010-04-16'),
     ('2010-04-17'),
     ('2010-04-18'),
     ('2010-04-19'),
     ('2010-04-20'),
     ('2010-04-21'),
     ('2010-04-22'),
     ('2010-04-23'),
     ('2010-04-24'),
     ('2010-04-25'),
     ('2010-04-26'),
     ('2010-04-28'),
     ('2010-04-30'),
     ('2010-05-01'),
     ('2010-05-02'),
     ('2010-05-03'),
     ('2010-05-04'),
     ('2010-05-05'),
     ('2010-05-06'),
     ('2010-05-07'),
     ('2010-05-08'),
     ('2010-05-09'),
     ('2010-05-10'),
     ('2010-05-11'),
     ('2010-05-13'),
     ('2010-05-14'),
     ('2010-05-15'),
     ('2010-05-16'),
     ('2010-05-17'),
     ('2010-05-18'),
     ('2010-05-19'),
     ('2010-05-22'),
     ('2010-05-23'),
     ('2010-05-24'),
     ('2010-05-25'),
     ('2010-05-26'),
     ('2010-05-27'),
     ('2010-05-28'),
     ('2010-05-29'),
     ('2010-05-30'),
     ('2010-05-31'),
     ('2010-06-01'),
     ('2010-06-02'),
     ('2010-06-03'),
     ('2010-06-04'),
     ('2010-06-05'),
     ('2010-06-06'),
     ('2010-06-07'),
     ('2010-06-08'),
     ('2010-06-09'),
     ('2010-06-10'),
     ('2010-06-11'),
     ('2010-06-12'),
     ('2010-06-13'),
     ('2010-06-14'),
     ('2010-06-15'),
     ('2010-06-16'),
     ('2010-06-17'),
     ('2010-06-18'),
     ('2010-06-19'),
     ('2010-06-20'),
     ('2010-06-21'),
     ('2010-06-22'),
     ('2010-06-23'),
     ('2010-06-24'),
     ('2010-06-25'),
     ('2010-06-26'),
     ('2010-06-27'),
     ('2010-06-28'),
     ('2010-06-29'),
     ('2010-06-30'),
     ('2010-07-01'),
     ('2010-07-02'),
     ('2010-07-03'),
     ('2010-07-04'),
     ('2010-07-05'),
     ('2010-07-06'),
     ('2010-07-07'),
     ('2010-07-08'),
     ('2010-07-09'),
     ('2010-07-10'),
     ('2010-07-11'),
     ('2010-07-12'),
     ('2010-07-13'),
     ('2010-07-17'),
     ('2010-07-18'),
     ('2010-07-19'),
     ('2010-07-21'),
     ('2010-07-22'),
     ('2010-07-24'),
     ('2010-07-25'),
     ('2010-07-26'),
     ('2010-07-27'),
     ('2010-07-28'),
     ('2010-07-29'),
     ('2010-07-30'),
     ('2010-07-31'),
     ('2010-08-01'),
     ('2010-08-02'),
     ('2010-08-03'),
     ('2010-08-04'),
     ('2010-08-05'),
     ('2010-08-06'),
     ('2010-08-07'),
     ('2010-08-08'),
     ('2010-08-09'),
     ('2010-08-10'),
     ('2010-08-11'),
     ('2010-08-12'),
     ('2010-08-13'),
     ('2010-08-14'),
     ('2010-08-15'),
     ('2010-08-16'),
     ('2010-08-17'),
     ('2010-08-18'),
     ('2010-08-19'),
     ('2010-08-20'),
     ('2010-08-21'),
     ('2010-08-22'),
     ('2010-08-23'),
     ('2010-08-24'),
     ('2010-08-25'),
     ('2010-08-26'),
     ('2010-08-27'),
     ('2010-08-28'),
     ('2010-08-29'),
     ('2010-08-30'),
     ('2010-08-31'),
     ('2010-09-01'),
     ('2010-09-02'),
     ('2010-09-03'),
     ('2010-09-04'),
     ('2010-09-05'),
     ('2010-09-06'),
     ('2010-09-07'),
     ('2010-09-08'),
     ('2010-09-09'),
     ('2010-09-10'),
     ('2010-09-11'),
     ('2010-09-12'),
     ('2010-09-13'),
     ('2010-09-14'),
     ('2010-09-15'),
     ('2010-09-16'),
     ('2010-09-17'),
     ('2010-09-19'),
     ('2010-09-20'),
     ('2010-09-21'),
     ('2010-09-22'),
     ('2010-09-23'),
     ('2010-09-24'),
     ('2010-09-25'),
     ('2010-09-26'),
     ('2010-09-27'),
     ('2010-09-28'),
     ('2010-09-29'),
     ('2010-09-30'),
     ('2010-10-01'),
     ('2010-10-02'),
     ('2010-10-03'),
     ('2010-10-04'),
     ('2010-10-05'),
     ('2010-10-06'),
     ('2010-10-07'),
     ('2010-10-08'),
     ('2010-10-09'),
     ('2010-10-10'),
     ('2010-10-11'),
     ('2010-10-12'),
     ('2010-10-13'),
     ('2010-10-15'),
     ('2010-10-16'),
     ('2010-10-17'),
     ('2010-10-18'),
     ('2010-10-19'),
     ('2010-10-20'),
     ('2010-10-21'),
     ('2010-10-22'),
     ('2010-10-23'),
     ('2010-10-24'),
     ('2010-10-25'),
     ('2010-10-26'),
     ('2010-10-27'),
     ('2010-10-28'),
     ('2010-10-29'),
     ('2010-10-30'),
     ('2010-10-31'),
     ('2010-11-01'),
     ('2010-11-02'),
     ('2010-11-05'),
     ('2010-11-06'),
     ('2010-11-07'),
     ('2010-11-08'),
     ('2010-11-09'),
     ('2010-11-10'),
     ('2010-11-11'),
     ('2010-11-12'),
     ('2010-11-13'),
     ('2010-11-16'),
     ('2010-11-17'),
     ('2010-11-20'),
     ('2010-11-21'),
     ('2010-11-22'),
     ('2010-11-23'),
     ('2010-11-24'),
     ('2010-11-25'),
     ('2010-11-27'),
     ('2010-11-28'),
     ('2010-11-29'),
     ('2010-11-30'),
     ('2010-12-01'),
     ('2010-12-03'),
     ('2010-12-04'),
     ('2010-12-06'),
     ('2010-12-07'),
     ('2010-12-08'),
     ('2010-12-09'),
     ('2010-12-10'),
     ('2010-12-11'),
     ('2010-12-12'),
     ('2010-12-13'),
     ('2010-12-14'),
     ('2010-12-15'),
     ('2010-12-16'),
     ('2010-12-17'),
     ('2010-12-18'),
     ('2010-12-19'),
     ('2010-12-23'),
     ('2010-12-24'),
     ('2010-12-27'),
     ('2010-12-28'),
     ('2010-12-29'),
     ('2010-12-30'),
     ('2010-12-31'),
     ('2011-01-01'),
     ('2011-01-02'),
     ('2011-01-03'),
     ('2011-01-04'),
     ('2011-01-05'),
     ('2011-01-06'),
     ('2011-01-07'),
     ('2011-01-08'),
     ('2011-01-09'),
     ('2011-01-10'),
     ('2011-01-11'),
     ('2011-01-14'),
     ('2011-01-15'),
     ('2011-01-16'),
     ('2011-01-17'),
     ('2011-01-18'),
     ('2011-01-19'),
     ('2011-01-20'),
     ('2011-01-21'),
     ('2011-01-22'),
     ('2011-01-23'),
     ('2011-01-24'),
     ('2011-01-25'),
     ('2011-01-27'),
     ('2011-01-28'),
     ('2011-01-29'),
     ('2011-01-30'),
     ('2011-01-31'),
     ('2011-02-01'),
     ('2011-02-02'),
     ('2011-02-03'),
     ('2011-02-04'),
     ('2011-02-05'),
     ('2011-02-06'),
     ('2011-02-07'),
     ('2011-02-08'),
     ('2011-02-09'),
     ('2011-02-10'),
     ('2011-02-13'),
     ('2011-02-14'),
     ('2011-02-15'),
     ('2011-02-16'),
     ('2011-02-19'),
     ('2011-02-20'),
     ('2011-02-21'),
     ('2011-02-22'),
     ('2011-02-23'),
     ('2011-02-24'),
     ('2011-02-25'),
     ('2011-02-26'),
     ('2011-02-27'),
     ('2011-02-28'),
     ('2011-03-01'),
     ('2011-03-02'),
     ('2011-03-03'),
     ('2011-03-04'),
     ('2011-03-05'),
     ('2011-03-06'),
     ('2011-03-09'),
     ('2011-03-10'),
     ('2011-03-12'),
     ('2011-03-13'),
     ('2011-03-14'),
     ('2011-03-16'),
     ('2011-03-17'),
     ('2011-03-18'),
     ('2011-03-19'),
     ('2011-03-20'),
     ('2011-03-21'),
     ('2011-03-22'),
     ('2011-03-23'),
     ('2011-03-24'),
     ('2011-03-25'),
     ('2011-03-26'),
     ('2011-03-27'),
     ('2011-03-28'),
     ('2011-03-30'),
     ('2011-03-31'),
     ('2011-04-01'),
     ('2011-04-02'),
     ('2011-04-03'),
     ('2011-04-04'),
     ('2011-04-05'),
     ('2011-04-06'),
     ('2011-04-07'),
     ('2011-04-08'),
     ('2011-04-09'),
     ('2011-04-10'),
     ('2011-04-11'),
     ('2011-04-12'),
     ('2011-04-13'),
     ('2011-04-15'),
     ('2011-04-16'),
     ('2011-04-17'),
     ('2011-04-18'),
     ('2011-04-19'),
     ('2011-04-20'),
     ('2011-04-21'),
     ('2011-04-22'),
     ('2011-04-23'),
     ('2011-04-24'),
     ('2011-04-25'),
     ('2011-04-26'),
     ('2011-04-27'),
     ('2011-04-29'),
     ('2011-04-30'),
     ('2011-05-01'),
     ('2011-05-02'),
     ('2011-05-03'),
     ('2011-05-04'),
     ('2011-05-05'),
     ('2011-05-06'),
     ('2011-05-07'),
     ('2011-05-08'),
     ('2011-05-09'),
     ('2011-05-10'),
     ('2011-05-11'),
     ('2011-05-12'),
     ('2011-05-13'),
     ('2011-05-14'),
     ('2011-05-15'),
     ('2011-05-16'),
     ('2011-05-17'),
     ('2011-05-18'),
     ('2011-05-19'),
     ('2011-05-20'),
     ('2011-05-21'),
     ('2011-05-22'),
     ('2011-05-23'),
     ('2011-05-24'),
     ('2011-05-25'),
     ('2011-05-26'),
     ('2011-05-27'),
     ('2011-05-28'),
     ('2011-05-29'),
     ('2011-05-30'),
     ('2011-05-31'),
     ('2011-06-01'),
     ('2011-06-02'),
     ('2011-06-03'),
     ('2011-06-04'),
     ('2011-06-05'),
     ('2011-06-06'),
     ('2011-06-07'),
     ('2011-06-08'),
     ('2011-06-09'),
     ('2011-06-10'),
     ('2011-06-11'),
     ('2011-06-12'),
     ('2011-06-13'),
     ('2011-06-14'),
     ('2011-06-15'),
     ('2011-06-17'),
     ('2011-06-18'),
     ('2011-06-19'),
     ('2011-06-20'),
     ('2011-06-21'),
     ('2011-06-25'),
     ('2011-06-26'),
     ('2011-06-27'),
     ('2011-06-28'),
     ('2011-06-29'),
     ('2011-07-01'),
     ('2011-07-02'),
     ('2011-07-03'),
     ('2011-07-04'),
     ('2011-07-05'),
     ('2011-07-06'),
     ('2011-07-07'),
     ('2011-07-08'),
     ('2011-07-09'),
     ('2011-07-10'),
     ('2011-07-11'),
     ('2011-07-12'),
     ('2011-07-13'),
     ('2011-07-14'),
     ('2011-07-15'),
     ('2011-07-16'),
     ('2011-07-17'),
     ('2011-07-18'),
     ('2011-07-19'),
     ('2011-07-20'),
     ('2011-07-21'),
     ('2011-07-23'),
     ('2011-07-24'),
     ('2011-07-25'),
     ('2011-07-26'),
     ('2011-07-27'),
     ('2011-07-28'),
     ('2011-07-29'),
     ('2011-07-30'),
     ('2011-07-31'),
     ('2011-08-01'),
     ('2011-08-02'),
     ('2011-08-03'),
     ('2011-08-04'),
     ('2011-08-05'),
     ('2011-08-06'),
     ('2011-08-07'),
     ('2011-08-08'),
     ('2011-08-09'),
     ('2011-08-11'),
     ('2011-08-12'),
     ('2011-08-13'),
     ('2011-08-14'),
     ('2011-08-15'),
     ('2011-08-16'),
     ('2011-08-17'),
     ('2011-08-18'),
     ('2011-08-19'),
     ('2011-08-20'),
     ('2011-08-21'),
     ('2011-08-22'),
     ('2011-08-23'),
     ('2011-08-24'),
     ('2011-08-25'),
     ('2011-08-26'),
     ('2011-08-27'),
     ('2011-08-28'),
     ('2011-08-29'),
     ('2011-08-30'),
     ('2011-08-31'),
     ('2011-09-02'),
     ('2011-09-03'),
     ('2011-09-04'),
     ('2011-09-05'),
     ('2011-09-06'),
     ('2011-09-07'),
     ('2011-09-08'),
     ('2011-09-09'),
     ('2011-09-10'),
     ('2011-09-11'),
     ('2011-09-12'),
     ('2011-09-13'),
     ('2011-09-14'),
     ('2011-09-15'),
     ('2011-09-16'),
     ('2011-09-17'),
     ('2011-09-18'),
     ('2011-09-19'),
     ('2011-09-20'),
     ('2011-09-21'),
     ('2011-09-22'),
     ('2011-09-23'),
     ('2011-09-24'),
     ('2011-09-25'),
     ('2011-09-26'),
     ('2011-09-27'),
     ('2011-09-28'),
     ('2011-10-01'),
     ('2011-10-02'),
     ('2011-10-03'),
     ('2011-10-06'),
     ('2011-10-07'),
     ('2011-10-08'),
     ('2011-10-09'),
     ('2011-10-10'),
     ('2011-10-11'),
     ('2011-10-12'),
     ('2011-10-13'),
     ('2011-10-14'),
     ('2011-10-15'),
     ('2011-10-16'),
     ('2011-10-17'),
     ('2011-10-18'),
     ('2011-10-19'),
     ('2011-10-20'),
     ('2011-10-21'),
     ('2011-10-22'),
     ('2011-10-23'),
     ('2011-10-24'),
     ('2011-10-25'),
     ('2011-10-26'),
     ('2011-10-27'),
     ('2011-10-28'),
     ('2011-10-29'),
     ('2011-10-30'),
     ('2011-10-31'),
     ('2011-11-01'),
     ('2011-11-02'),
     ('2011-11-03'),
     ('2011-11-04'),
     ('2011-11-05'),
     ('2011-11-06'),
     ('2011-11-07'),
     ('2011-11-08'),
     ('2011-11-09'),
     ('2011-11-10'),
     ('2011-11-11'),
     ('2011-11-12'),
     ('2011-11-13'),
     ('2011-11-14'),
     ('2011-11-15'),
     ('2011-11-16'),
     ('2011-11-17'),
     ('2011-11-18'),
     ('2011-11-19'),
     ('2011-11-20'),
     ('2011-11-21'),
     ('2011-11-22'),
     ('2011-11-23'),
     ('2011-11-24'),
     ('2011-11-25'),
     ('2011-11-26'),
     ('2011-11-27'),
     ('2011-11-28'),
     ('2011-11-29'),
     ('2011-11-30'),
     ('2011-12-01'),
     ('2011-12-02'),
     ('2011-12-03'),
     ('2011-12-04'),
     ('2011-12-05'),
     ('2011-12-06'),
     ('2011-12-07'),
     ('2011-12-08'),
     ('2011-12-09'),
     ('2011-12-10'),
     ('2011-12-11'),
     ('2011-12-12'),
     ('2011-12-13'),
     ('2011-12-14'),
     ('2011-12-15'),
     ('2011-12-16'),
     ('2011-12-17'),
     ('2011-12-18'),
     ('2011-12-19'),
     ('2011-12-20'),
     ('2011-12-21'),
     ('2011-12-22'),
     ('2011-12-23'),
     ('2011-12-24'),
     ('2011-12-25'),
     ('2011-12-26'),
     ('2011-12-27'),
     ('2011-12-28'),
     ('2011-12-29'),
     ('2011-12-30'),
     ('2011-12-31'),
     ('2012-01-01'),
     ('2012-01-02'),
     ('2012-01-03'),
     ('2012-01-04'),
     ('2012-01-06'),
     ('2012-01-07'),
     ('2012-01-08'),
     ('2012-01-10'),
     ('2012-01-11'),
     ('2012-01-12'),
     ('2012-01-14'),
     ('2012-01-15'),
     ('2012-01-16'),
     ('2012-01-17'),
     ('2012-01-18'),
     ('2012-01-19'),
     ('2012-01-20'),
     ('2012-01-21'),
     ('2012-01-22'),
     ('2012-01-23'),
     ('2012-01-24'),
     ('2012-01-25'),
     ('2012-01-26'),
     ('2012-01-27'),
     ('2012-01-28'),
     ('2012-01-29'),
     ('2012-01-30'),
     ('2012-01-31'),
     ('2012-02-01'),
     ('2012-02-02'),
     ('2012-02-03'),
     ('2012-02-04'),
     ('2012-02-05'),
     ('2012-02-06'),
     ('2012-02-07'),
     ('2012-02-08'),
     ('2012-02-09'),
     ('2012-02-10'),
     ('2012-02-11'),
     ('2012-02-12'),
     ('2012-02-13'),
     ('2012-02-14'),
     ('2012-02-15'),
     ('2012-02-16'),
     ('2012-02-17'),
     ('2012-02-18'),
     ('2012-02-19'),
     ('2012-02-20'),
     ('2012-02-21'),
     ('2012-02-22'),
     ('2012-02-23'),
     ('2012-02-24'),
     ('2012-02-25'),
     ('2012-02-26'),
     ('2012-02-27'),
     ('2012-02-28'),
     ('2012-02-29'),
     ('2012-03-01'),
     ('2012-03-02'),
     ('2012-03-03'),
     ('2012-03-04'),
     ('2012-03-05'),
     ('2012-03-06'),
     ('2012-03-07'),
     ('2012-03-08'),
     ('2012-03-09'),
     ('2012-03-10'),
     ('2012-03-11'),
     ('2012-03-12'),
     ('2012-03-13'),
     ('2012-03-14'),
     ('2012-03-15'),
     ('2012-03-16'),
     ('2012-03-17'),
     ('2012-03-18'),
     ('2012-03-19'),
     ('2012-03-20'),
     ('2012-03-21'),
     ('2012-03-22'),
     ('2012-03-23'),
     ('2012-03-24'),
     ('2012-03-25'),
     ('2012-03-26'),
     ('2012-03-27'),
     ('2012-03-28'),
     ('2012-03-29'),
     ('2012-03-30'),
     ('2012-03-31'),
     ('2012-04-01'),
     ('2012-04-02'),
     ('2012-04-03'),
     ('2012-04-04'),
     ('2012-04-05'),
     ('2012-04-06'),
     ('2012-04-07'),
     ('2012-04-08'),
     ('2012-04-09'),
     ('2012-04-10'),
     ('2012-04-11'),
     ('2012-04-12'),
     ('2012-04-13'),
     ('2012-04-14'),
     ('2012-04-15'),
     ('2012-04-16'),
     ('2012-04-17'),
     ('2012-04-18'),
     ('2012-04-19'),
     ('2012-04-20'),
     ('2012-04-21'),
     ('2012-04-22'),
     ('2012-04-23'),
     ('2012-04-24'),
     ('2012-04-25'),
     ('2012-04-26'),
     ('2012-04-27'),
     ('2012-04-28'),
     ('2012-04-29'),
     ('2012-04-30'),
     ('2012-05-01'),
     ('2012-05-02'),
     ('2012-05-03'),
     ('2012-05-04'),
     ('2012-05-05'),
     ('2012-05-06'),
     ('2012-05-07'),
     ('2012-05-08'),
     ('2012-05-09'),
     ('2012-05-10'),
     ('2012-05-11'),
     ('2012-05-12'),
     ('2012-05-13'),
     ('2012-05-14'),
     ('2012-05-15'),
     ('2012-05-16'),
     ('2012-05-17'),
     ('2012-05-18'),
     ('2012-05-19'),
     ('2012-05-20'),
     ('2012-05-21'),
     ('2012-05-22'),
     ('2012-05-23'),
     ('2012-05-24'),
     ('2012-05-25'),
     ('2012-05-26'),
     ('2012-05-27'),
     ('2012-05-28'),
     ('2012-05-29'),
     ('2012-05-30'),
     ('2012-05-31'),
     ('2012-06-01'),
     ('2012-06-02'),
     ('2012-06-03'),
     ('2012-06-04'),
     ('2012-06-05'),
     ('2012-06-06'),
     ('2012-06-07'),
     ('2012-06-10'),
     ('2012-06-11'),
     ('2012-06-12'),
     ('2012-06-13'),
     ('2012-06-14'),
     ('2012-06-15'),
     ('2012-06-16'),
     ('2012-06-17'),
     ('2012-06-18'),
     ('2012-06-19'),
     ('2012-06-20'),
     ('2012-06-21'),
     ('2012-06-22'),
     ('2012-06-23'),
     ('2012-06-24'),
     ('2012-06-25'),
     ('2012-06-26'),
     ('2012-06-27'),
     ('2012-06-28'),
     ('2012-06-29'),
     ('2012-06-30'),
     ('2012-07-01'),
     ('2012-07-02'),
     ('2012-07-03'),
     ('2012-07-04'),
     ('2012-07-05'),
     ('2012-07-06'),
     ('2012-07-07'),
     ('2012-07-08'),
     ('2012-07-10'),
     ('2012-07-11'),
     ('2012-07-12'),
     ('2012-07-13'),
     ('2012-07-14'),
     ('2012-07-15'),
     ('2012-07-16'),
     ('2012-07-17'),
     ('2012-07-18'),
     ('2012-07-19'),
     ('2012-07-20'),
     ('2012-07-21'),
     ('2012-07-22'),
     ('2012-07-23'),
     ('2012-07-24'),
     ('2012-07-25'),
     ('2012-07-26'),
     ('2012-07-27'),
     ('2012-07-28'),
     ('2012-07-29'),
     ('2012-07-30'),
     ('2012-07-31'),
     ('2012-08-01'),
     ('2012-08-02'),
     ('2012-08-03'),
     ('2012-08-04'),
     ('2012-08-05'),
     ('2012-08-06'),
     ('2012-08-07'),
     ('2012-08-08'),
     ('2012-08-09'),
     ('2012-08-10'),
     ('2012-08-11'),
     ('2012-08-12'),
     ('2012-08-13'),
     ('2012-08-14'),
     ('2012-08-15'),
     ('2012-08-16'),
     ('2012-08-17'),
     ('2012-08-20'),
     ('2012-08-21'),
     ('2012-08-22'),
     ('2012-08-23'),
     ('2012-08-24'),
     ('2012-08-25'),
     ('2012-08-26'),
     ('2012-08-27'),
     ('2012-08-28'),
     ('2012-08-29'),
     ('2012-08-30'),
     ('2012-08-31'),
     ('2012-09-01'),
     ('2012-09-02'),
     ('2012-09-03'),
     ('2012-09-04'),
     ('2012-09-05'),
     ('2012-09-06'),
     ('2012-09-07'),
     ('2012-09-08'),
     ('2012-09-09'),
     ('2012-09-10'),
     ('2012-09-11'),
     ('2012-09-12'),
     ('2012-09-13'),
     ('2012-09-14'),
     ('2012-09-15'),
     ('2012-09-16'),
     ('2012-09-17'),
     ('2012-09-18'),
     ('2012-09-19'),
     ('2012-09-20'),
     ('2012-09-21'),
     ('2012-09-22'),
     ('2012-09-23'),
     ('2012-09-24'),
     ('2012-09-25'),
     ('2012-09-26'),
     ('2012-09-27'),
     ('2012-09-28'),
     ('2012-09-29'),
     ('2012-09-30'),
     ('2012-10-01'),
     ('2012-10-02'),
     ('2012-10-03'),
     ('2012-10-04'),
     ('2012-10-05'),
     ('2012-10-06'),
     ('2012-10-07'),
     ('2012-10-08'),
     ('2012-10-09'),
     ('2012-10-10'),
     ('2012-10-11'),
     ('2012-10-12'),
     ('2012-10-13'),
     ('2012-10-14'),
     ('2012-10-15'),
     ('2012-10-16'),
     ('2012-10-17'),
     ('2012-10-18'),
     ('2012-10-19'),
     ('2012-10-20'),
     ('2012-10-21'),
     ('2012-10-22'),
     ('2012-10-23'),
     ('2012-10-24'),
     ('2012-10-25'),
     ('2012-10-26'),
     ('2012-10-27'),
     ('2012-10-28'),
     ('2012-10-29'),
     ('2012-10-30'),
     ('2012-10-31'),
     ('2012-11-01'),
     ('2012-11-02'),
     ('2012-11-03'),
     ('2012-11-04'),
     ('2012-11-05'),
     ('2012-11-06'),
     ('2012-11-07'),
     ('2012-11-08'),
     ('2012-11-09'),
     ('2012-11-10'),
     ('2012-11-11'),
     ('2012-11-12'),
     ('2012-11-13'),
     ('2012-11-14'),
     ('2012-11-15'),
     ('2012-11-16'),
     ('2012-11-17'),
     ('2012-11-18'),
     ('2012-11-19'),
     ('2012-11-20'),
     ('2012-11-21'),
     ('2012-11-22'),
     ('2012-11-23'),
     ('2012-11-24'),
     ('2012-11-25'),
     ('2012-11-26'),
     ('2012-11-27'),
     ('2012-11-28'),
     ('2012-11-29'),
     ('2012-11-30'),
     ('2012-12-01'),
     ('2012-12-02'),
     ('2012-12-03'),
     ('2012-12-04'),
     ('2012-12-05'),
     ('2012-12-08'),
     ('2012-12-09'),
     ('2012-12-10'),
     ('2012-12-11'),
     ('2012-12-12'),
     ('2012-12-13'),
     ('2012-12-14'),
     ('2012-12-15'),
     ('2012-12-16'),
     ('2012-12-17'),
     ...]




```python
session.query(Station.station).all()
```




    [('USC00519397'),
     ('USC00513117'),
     ('USC00514830'),
     ('USC00517948'),
     ('USC00518838'),
     ('USC00519523'),
     ('USC00519281'),
     ('USC00511918'),
     ('USC00516128'),
     ('USC00519397'),
     ('USC00513117'),
     ('USC00514830'),
     ('USC00517948'),
     ('USC00518838'),
     ('USC00519523'),
     ('USC00519281'),
     ('USC00511918'),
     ('USC00516128')]



## Precipitation Analysis:

Design a query to retrieve the last 12 months of precipitation data.

Select only the date and prcp values.

Load the query results into a Pandas DataFrame and set the index to the date column.

Plot the results using the DataFrame plot method.




```python
import datetime as dt
import numpy as np
import pandas as pd
import matplotlib
matplotlib.use('nbagg')
from matplotlib import style
style.use('fivethirtyeight')
import matplotlib.pyplot as plt

date1 = dt.datetime(2016, 1,1)
date2 = dt.datetime(2016,12,31)
```


```python
result = session.query(Measurements.date, Measurements.prcp).\
           filter(Measurements.date >= date1).\
           filter(Measurements.date <= date2).all()
```


```python
df = pd.DataFrame(result, columns = ["date", "prcp"])
df['date'] = pd.to_datetime(df['date'])

df = df.set_index("date")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>prcp</th>
    </tr>
    <tr>
      <th>date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-01-02</th>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-01-03</th>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-01-04</th>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-01-05</th>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-01-06</th>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
fig, ax = plt.subplots()
ax.plot(df.index,df['prcp'] , color="red")
ax.set_xlabel("Date")
ax.set_ylabel("Precipitation")
ax.set_title("Precipitation")
fig.tight_layout()
plt.show()
```


    <IPython.core.display.Javascript object>



<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAoAAAAHgCAYAAAA10dzkAAAAAXNSR0IArs4c6QAAQABJREFUeAHsnQecJEXZxmtmNqcjHBwcHBxHligCRuAQEASJCggiLIoKKqB+n4pKWJEgoPgpoiACCwKCIEFFkXhkQXLOLBwcHBwHl+/2NnzPOzu129vTebp7Ojzv7/dsV1dVV/hX78w71d3VStFIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARIgARSTaAHrR+uKNUdyXjjZ1TGSLZptx50IIxzrrdSTh+2NBIggRwQKOagj+wiCZAACZAACZAACZCAgQAdQAMMBkmABFJLoBctl5mwPoiWHALT0RQ9QylhGgmQQEIINCSkHWwGCZAACcRFYHpcFaWonm60VUQjARLICQHOAOZkoNlNEiABEiABEiABEtAE6ABqEtySAAmQAAmQAAmQQE4I0AHMyUCzm54JNCLn16FbodlQP/QOdBt0JCTpXq0LGU+CnoQWQB9A90JHQG7/ex9Gngug56CF0DLoTehR6I/QAVAzZGcTkPAj6B7oXUj6If35F3QoVILsrA8Jct9WLyQmbbkQegVaAknaCtDLlfDD2LpZGzIIAzn2r6bMwuLT0C8g4TMHWg4Jr8cgiV8LsrIeREqZh1US167sS5xRleTyZkYlTbZO9jEk9kLS78XQfOgp6GzIrj1IUlMhXXc3wmI7QddDsyAZy5lQL7QBFKbJOfE96CFoHiTnjjA8DmqB7KwXCdLmPsjO9kbCtdDr0FJoEfQqdD90JjQd0jYVASnvDh1RCUucUd2GdB1cGQEp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" width="640">


## Station Analysis

Design a query to calculate the total number of stations.

Design a query to find the most active stations.

List the stations and observation counts in descending order
Which station has the highest number of observations?
Design a query to retrieve the last 12 months of temperature observation data (tobs).

Filter by the station with the highest number of observations.
Plot the results as a histogram with bins=12.



```python
session.query(func.count(Station.station)).all()
```




    [(18)]




```python
dt.date(2017,8,23) - dt.timedelta(days=365)
```




    datetime.date(2016, 8, 23)




```python
sel = [Station.station, func.count(Measurements.tobs)]
session.query(*sel).filter(Station.station == Measurements.station ).\
                group_by(Station.station).\
                order_by(func.count(Measurements.tobs).desc()).limit(1).all()               
```




    [('USC00519281', 11088)]




```python
sel = [Station.station, func.sum(Measurements.tobs)]
date1= dt.datetime(2017,8,23)
date2 = date1 - dt.timedelta(days=365)
session.query(*sel).filter(Station.station == Measurements.station ).\
                  filter(Measurements.date <= date1).\
                 filter(Measurements.date >= date2).\
                group_by(Station.station).\
                order_by(func.sum(Measurements.tobs).desc()).all()
```




    [('USC00519397', 107660.0),
     ('USC00519281', 102628.0),
     ('USC00513117', 100232.0),
     ('USC00519523', 96404.0),
     ('USC00516128', 94184.0),
     ('USC00514830', 81504.0),
     ('USC00517948', 17732.0)]




```python
result1= session.query(*sel).filter(Station.station == Measurements.station ).\
                group_by(Station.station).\
                order_by(func.count(Measurements.tobs).desc()).all()               
```


```python
df1 = pd.DataFrame(result1, columns = ['station', 'number of obvervation'])
df1 = df1.set_index('station')
df1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>number of obvervation</th>
    </tr>
    <tr>
      <th>station</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>USC00519281</th>
      <td>794608.0</td>
    </tr>
    <tr>
      <th>USC00513117</th>
      <td>783760.0</td>
    </tr>
    <tr>
      <th>USC00519397</th>
      <td>800820.0</td>
    </tr>
    <tr>
      <th>USC00519523</th>
      <td>766792.0</td>
    </tr>
    <tr>
      <th>USC00516128</th>
      <td>704116.0</td>
    </tr>
    <tr>
      <th>USC00514830</th>
      <td>579652.0</td>
    </tr>
    <tr>
      <th>USC00511918</th>
      <td>552764.0</td>
    </tr>
    <tr>
      <th>USC00517948</th>
      <td>203772.0</td>
    </tr>
    <tr>
      <th>USC00518838</th>
      <td>99420.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
n_bins = 8
x = df1.index
y = df1['number of obvervation']
fig, axes = plt.subplots(figsize=(10,5))

axes.bar(x,y )
ax.set_title("observation histgram")
fig.show()
```


    <IPython.core.display.Javascript object>



<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA+gAAAH0CAYAAACuKActAAAAAXNSR0IArs4c6QAAQABJREFUeAHs3Qu8bed8L/y17djJQSJpe7qJxiXEtUV7VLRuO26ppgdHq0EpQY7youg5LkWIO6eHlnopjkTcUtSth0ocTeIuipaihDTktZO4hcRl2+zk/f33nk/OyMhcc6255lgrc639fT6f3xpjPON5njHGd849937WmHPuhQWFAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAAECBAgQIECAAIG9TmDTXnfFA1zwpZdeuvniiy8+rDvUpk2bvpftS7t11gkQIECAAAECBAgQIEBg1QQ2ZW72C93R999//7MyN9vVrVtP6/usp5Odl3Otyfkll1zypXk5H+dBgAABAgQIECBAgAABAgsLmavdLA7/tl4trrJeT9x5EyBAgAABAgQIECBAgACBjSRggr6RHk3XQoAAAQIECBAgQIAAAQLrVsAEfd0+dE6cAAECBAgQIECAAAECBDaSgAn6Ch7N0RfCraDn3ttlx44dC2efffZCLZXVE+C8erbdkTl3NVZvnfPq2XZH5tzVWL11zqtn2x2Zc1dj9dY5r55td2TOXY3lr6/3uZoJ+vIf625L39be1Vjm+q5d6/bLFJd5hfPRjPPaPA6cOa+NwNocxfOZ89oIrM1RPJ85r43A2hzF83lFzut6rmaCvqLHXCcCBAgQIECAAAECBAgQIDCsgAn6sJ5GI0CAAAECBAgQIECAAAECKxIwQV8Rm04ECBAgQIAAAQIECBAgQGBYARP0YT2NRoAAAQIECBAgQIAAAQIEViRggr4iNp0IECBAgAABAgQIECBAgMCwAibow3oajQABAgQIECBAgAABAgQIrEjABH1FbDoRIECAAAECBAgQIECAAIFhBUzQh/U0GgECBAgQIECAAAECBAgQWJGACfqK2HQiQIAAAQIECBAgQIAAAQLDCoyboG/KIe6bnJacl/w4+XLyN8mhSb/sm4rjkq8kO5Lq89rkWsli5YHZcWbyo+TC5H3JbZLFym9mR7WpttWn+tYYi5U6dp1DnUudU51bneOWZFxZyTWMG0cdAQIECBAgQIAAAQIECBBYkcC4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2dxdHpmfj0vq7nUtj0r+Pqm3oH8x6Zc3pqIm/LXvocnDki8nNemuff1S7Wqsekt+9fvTpD7zXseqY/fLSq6hP4ZtAgQIECBAgAABAgQIECCwYoHl3kF/aI5QWazUW9CfOMpibbr1dQf85aN06yetvz87K8st9Vb3+y23cdpNew1TDK0pAQIECBAgQIAAAQIECBCYLDDEHfTJR7CXAAECBAgQIECAAAECBAgQWFLABH1JIg0IECBAgAABAgQIECBAgMDqC5igr76xIxAgQIAAAQIECBAgQIAAgSUFTNCXJNKAAAECBAgQIECAAAECBAisvoAJ+uobOwIBAgQIECBAgAABAgQIEFhSwAR9SSINCBAgQIAAAQIECBAgQIDA6guYoK++sSMQIECAAAECBAgQIECAAIElBUzQlyTSgAABAgQIECBAgAABAgQIrL6ACfrqGzsCAQIECBAgQIAAAQIECBBYUsAEfUkiDQgQIECAAAECBAgQIECAwOoLmKCvvrEjECBAgAABAgQIECBAgACBJQVM0Jck0oAAAQIECBAgQIAAAQIECKy+gAn66hs7AgECBAgQIECAAAECBAgQWFLABH1JIg0IECBAgAABAgQIECBAgMDqC5igr76xIxAgQIAAAQIECBAgQIAAgSUFTNCXJNKAAAECBAgQIECAAAECBAisvoAJ+uobOwIBAgQIECBAgAABAgQIEFhSwAR9SSINCBAgQIAAAQIECBAgQIDA6guYoK++sSMQIECAAAECBAgQIECAAIElBUzQlyTSgAABAgQIECBAgAABAgQIrL6ACfrqGzsCAQIECBAgQIAAAQIECBBYUsAEfUkiDQgQIECAAAECBAgQIECAwOoLmKCvvrEjECBAgAABAgQIECBAgACBJQVM0Jck0oAAAQIECBAgQIAAAQIECKy+gAn66hs7AgECBAgQIECAAAECBAgQWFLABH1JIg0IECBAgAABAgQIECBAgMDqC5igr76xIxAgQIAAAQIECBAgQIAAgSUFTNCXJNKAAAECBAgQIECAAAECBAisvoAJ+uobOwIBAgQIECBAgAABAgQIEFhSwAR9SSINCBAgQIAAAQIECBAgQIDA6guYoK++sSMQIECAAAECBAgQIECAAIElBUzQlyTSgAABAgQIECBAgAABAgQIrL6ACfrqGzsCAQIECBAgQIAAAQIECBBY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" width="1000">


# Temperature Analysis

Write a function called calc_temps that will accept a start date and end date in the format %Y-%m-%d and return the minimum, average, and maximum temperatures for that range of dates.

Use the calc_temps function to calculate the min, avg, and max temperatures for your trip using the matching dates from the previous year (i.e. use "2017-01-01" if your trip start date was "2018-01-01")

Plot the min, avg, and max temperature from your previous query as a bar chart.

Use the average temperature as the bar height.
Use the peak-to-peak (tmax-tmin) value as the y error bar (yerr).



```python
def stripdate(date):
    day = pd.to_numeric(pd.to_datetime(date).strftime("%d"))
    month= pd.to_numeric(pd.to_datetime(date).strftime("%m"))
    year = pd.to_numeric(pd.to_datetime(date).strftime("%Y"))
    
    Year = pd.to_numeric((dt.datetime(year, month, day) - dt.timedelta(days=365)).strftime("%Y"))
    Month= pd.to_numeric((dt.datetime(year, month, day) - dt.timedelta(days=365)).strftime("%m"))
    Day= pd.to_numeric((dt.datetime(year, month, day) - dt.timedelta(days=365)).strftime("%d"))
    
    return dt.datetime(Year, Month, Day).strftime("%Y-%m-%d")
```


```python
start_date = "2016-03-24"
end_date = "2016-04-09"
```


```python
def calc_temps(start_date,  end_date):
    
    Pre_start_date = stripdate(start_date)
    Pre_end_date = stripdate(end_date)
    
    result = session.query(func.avg(Measurements.prcp), func.min(Measurements.prcp), func.max(Measurements.prcp) ).\
           filter(Measurements.date >= Pre_start_date).\
           filter(Measurements.date <= Pre_end_date).all()
            
    return pd.DataFrame(result, columns= ['Avg', "MIN", "Max"])
        
    
    
    
    
```


```python
ptps = calc_temps(start_date,  end_date)
```


```python
import numpy as np

fig, ax = plt.subplots()

x = range(len(ptps))
ax.boxplot(ptps, patch_artist=True)
ax.set_title('Temp PTPs')
fig.tight_layout()
fig.show()
```


    <IPython.core.display.Javascript object>



<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAoAAAAHgCAYAAAA10dzkAAAAAXNSR0IArs4c6QAAQABJREFUeAHt3QvYJGdZJ/wOk8OA5ECATDLrLGG4shtgWQNy0nDIghJwPUTccDKQiSawCvsF5VKQ0yYajHwelksXRQISkQiISrj8liUIJNEAnwE+DmsEE4kDo5MDOUASYDLJkO9/T7pi2em333dmuvrtt+v3XNd/qvqpp5+q+lUcb6q6ewYDjQABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIzIvA0TmQu6aQmkdbWuCkbFrK+VvZ9pXkA8kLkwOTpk1631LzjfZ/vZksy5cno9ub17dl25eT9ya13/0SjQABAgQIEFhAgaNzTk0BsC/LmkdbWmBPCrnPZZp/O5xqT9631PX7euuwXp71pcaN9n8sYw9rvdcqAQJzLrD/nB+fwyNAYH4E/jmH8qgJh3NRtm1MticnThhX82grE3hjhr2rNfT+Wf/e5OeShyXfk3wwOS75aLLU9Tk42z6RVKti7czda/f+Y9e9u3b31Ph6X9MOzcr3J69INiT/KXlP8sxEI0CAAAECBHoksDXnWneGaqntvcBJeWtzh63uwo1rh6Tzb5Nm3CnjBrX66u5cM/bCVv+k1dp3856Tlhj4b9J/TWvck5YYp5sAgTkTuM+cHY/DIUCAAIHlBW7JkLNaw57VWp/lat3N/c3WDlfrOFqHYJUAgZUIKABXomQMAQJdCtSjxLcnVyX15YJvJn+f/F5ybLJUq7tSzR2q47K+Lnlp8v8mNydfTz6e/Jek3e6bF/VI89NJjali6tLkR5KlWs3f7Ouk4aCfzPLi5GvJt5MvJfXI9vBkFq3Os2kPaVZWYbnccTwxx3R+cmVS13ZHsi35TPKW5McTH0cKgkaAAAECBNaiwNYcdBVJtVxJq2+w/kHSFFbjlndmexVr41oVYs17vi/r9Rm45vXo8uzhBPV5tU9NGFcF5LjWLgCfnQHvTUb30byuR6L/YdwkK+xrn9fLJ7ynzqXZ5ycnjKtNh7XGXrjM2GZz7buZ/6Smc8zyCa1x7x7Z/rq8/k5rezPf6PLIkfd5SYAAAQIECKwRga05zvp/7LVcSfuzDGoKgUuyflry1OSxyU8ln0ua7XW3bbRVUdJsr7tQ9QWGupN4YvKY5IXJPybNmCpULk5uT34reVpSX6j4r0ndxatxdXfq6GS0HZeOZp7Lh+t1d/G5Sc1Rjz7/OGnG1BdhHpDsTWuf18snTPCD2dbsrywntcOysRl74aSBrW217+Y9J7X6R1fPaI37zdbG41v9dUe3CvkyPy6pzwqentQXXOoOrAIwCBoBAgQIEFiLAltz0FUw1HK5VsVeja27Qy9aYvAB6f+LpMZdn9Sj23aroqQpUGp5anvjcH1zllXUNXPUHcWnD7e1F+1ipblb2N5eRUt7X+/L6/u0BwzXf7E17s1jtq+kq31eL1/iDbXvjybNMb1siXFN92GtsRc2ncssa9/N/CctMfZ+6f+71rgfbo377WF/FdeHt/pHVw9OR11rjQABAgQIEFiDAltzzFUw1HJS2y8b6/NgNfaCSQOz7buT5hHiySNjqyhpCpQPjWxrv6wfTW7G/V57w8j654fjPjbSXy+PG26reeqO1VIFTZ3bZ4Zj6/OMVdzsaWuf18tH3lwF11OSv0yac7ou68vt57DW+AuzvpJW+272cdLIG+pbyHXXsz5H2Yz5P1lvF8V/Mtw2zjObNAIEVlOg/X+sq3kc9k2AQH8EHpFTPWZ4unUnbVL7p2y8ejigPue3VHvPUhvSX4Vd097brIxZNuM2j9nW7qqC8qZ2R2u9iqF3DF9/V5aTjrn1tiVX/0e2NAVWLetLFJcmP5BUq+Oo4uzWetFhe3/mbh/HN/K6fn+wHn9X+2ry48l36sWw1WPwao9L9uUzkbsn8QcBAtMVUABO19NsBAgsL1Cf8WvaaGHRLjKa9frB42qTPidWdxSXal9vbVjJuOXupl3emm/canv7fxw3YAp9/5g5fjOpwuqTU5hvb6ao6/Ol5KzkUck/JO32R3lRBeH9k88kda1fnNT/AKg7pRoBAqsosP8q7tuuCRDop8ARe3na95vwvm9N2Na+K7WScesmzFWbrl9mez2SbdoDm5W9XL4x73vX8L1VcNXnGW9I6g7cLNuZ2dnHhjus4yjH+mxfPeZeqlXR96KkPgt5aFJ3KptHyXUOFyX1pZ2LE40AgRkLKABnDG53BAjs/r2+huHZWbmqebHMsj57Nw+tCqBJbZp3t67Njv520s5mtK0e8e7NcdRnPP9X8rzkGUl9+/fByYOSnxzmT7I8Jbkj0QgQmJGAAnBG0HZDgMA9AnX3p2l1d25vCovm/aux3LDMTtt3OG9cZmwfNtcj+LcMU+f78ORHkv+W1Jd8npNckfxyohEgMCMBnwGcEbTdECBwj8Bn71kbDJ7ZWl8rq49f5kAf19pe34zV/rXAF/Py/07KsXmUXUWgRoDADAUUgDPEtisCBHYLVAFYjxSr1Y81b9y9tnb++NEc6gOWONx6/LtluO1bWX5iuG5xb4Fr0vV3w+56JKwRIDBDAQXgDLHtigCB3QL12PecoUX9VMr7k0kFQP1I8E8nS/32XjbNtB2SvdUjzXF/f/58+h87PJp3Ztn1z7MMdzWXi/+Sozp4wpEdlW3/Ybj9HyeMs4kAgQ4EfAawA1RTEiCwrMB5GfH0pP4ptXoUWI8Fq6iq37irzwjWN343J8cnP5HUFwfqW6P1u3er3T6VA6hHlnXn8reTLydHJPVFhvpiQ7X6JvBrd6/19486/3ck/09ySfKlpB751t3TxyT1GcCmQPzdrGsECMxQQAE4Q2y7IkDgXwlUwbQ9OTOpO4BVMCxVNO3Itp3JPLRfy0E8P6k7XE8ac0D1MzEnJjeO2da3rvvnhJ83zLhzr7vB5yZ/NG6jPgIEuhMY9wiju72ZmQABAv8icGdW65HpI5LfSuqzgTcnu5J6dPp3ybuTn0rqcWEVVvPQqmg5OdmS/FVShd7tyVXJryd1Pp9P+t5+KACnJlXclUf9pE1d89uS+tZv3fF9bLJU0Z9NGgECBAgQIEBg9QSOy67r9/8qzY8Zr97R2DMBAgT2UcAdwH0E9HYCBAgQIECAwFoTUACutSvmeAkQIECAAAEC+yigANxHQG8nQIAAAQIECKw1AQXgWrtijpcAAQIECBAgsI8CfgZmCHjXXXetu/XWW49pe+633371m2P1oW+NAIEeC/zwD//wAy69tH6icDB42MMedsjnPve5+l1CjQABAl0K7Jfa5PD2Dg4++OCrUpvULyXsc6t/tkiLwC233HLsd77znfoxWo0AAQIECBAgMHcC97nPfR5+yCGH1I+q73PzCHifCU1AgAABAgQIEFhbAgrAtXW9HC0BAgQIECBAYJ8FFID7TGgCAgQIECBAgMDaElAADq/X8Asfa+vqOVoCBOZWYMeOHYOrr756UEuNAAEC0xCYZq2iAPyXK+Lbvv9iYY0AgSkI7No1lS/rTeFITEGAwIIITK1WUQAuyH8RToMAAQIECBAgsFIBBeBKpYwjQIAAAQIECCyIgAJwQS6k0yBAgAABAgQIrFRAAbhSKeMIECBAgAABAgsioABckAvpNAgQIECAAAECKxVQAK5UyjgCBAgQIECAwIIIKAAX5EI6DQIECBAgQIDASgUUgCuVMo4AAQIECBAgsCACCsAFuZBOgwABAgQIECCwUgEF4EqljCNAgAABAgQILIiAAnBBLqTTIECAAAECBAisVKDLAvDf5CBennw4+WqyM7k2+bPkCcmetDrOlyVfSL6dfC35k+SYZKl2YjZcktyS3Dpcrz6NAAECBAgQINBrgS4LwP8W2f+RbE7+MvnN5LLkx5JPJM9JVtrekoG/k6wbLj+Y5Y8mn0oekYy2n0zHh5JHJn+YvCM5Nqm+2qYRIECAAAECBHorsF+HZ/7szF136v56ZB9PzuuPJnVXbmNyezKp/ads/FhS8/xg0ox/etarsKz+pyZNe0BWrk7uTB6TbEuqHZX8f8n6pIrSm5N72q233vrgXbt2XX9PhxUCBHolcO211w4q02o7d+4cXHfddYMNGzYMDjzwwGlNOzjyyCN3Z2oTmogAgTUjsG7duiMOPvjgqq32ue2/zzMsPcGfL7GpCraLk2ckj0o+nUxqZww3vjbLpvirrioiL0qemfy75Mqk2snJYcl/T5riL6uDa5I3Jb+W1Ji3JhoBAgR2C7zjHe8YvPGNb5x7jVe+8pWDX/qlX5r743SABAjMt0CXBeCkM79juLHu0i3XTsiAbyYfHzOwKQDrDmBTAJ4wHPfhJcZXAVjjFYBjgHQR6KvAaaedNnjWs541tdO/4oorBi996UsHb37zmwePfGR9GmU6re4AagQIENhXgdUoAP9tDvoHknrW8n+WOYHvyvajkr9Ndo0Ze9Wwr/1lkGa92dZ+W9PXjGlvu9f6jh077tWngwCBxRQ47LDDBpVptW9+s/5362Bw9NFHD4499thpTbt7Hn83TZXTZATmVmD9+vWdHdusC8ADciZ/lByU/GIyrqhL9z3t0OHaN+7p+dcr9Q3fas249vq499TfyLXP9vh6z9i2ffv2QT4XOHabTgIECEwSuOmmm3ZvruW2be1Po0x6l20ECBC4WyCf9xts3lxfWeimzbIArG8c/0HylOS8pArBuW4bN26c6+NzcAQIzK/A9dff/Z2yww8/fLBp06b5PVBHRoBALwVmVQDWt42r6DsleVfyX5OVtOYu3lJ37A4ZTtKMq5fNer3nxuH2ZlGPlNclzZimf+yyy1uvY3eokwCBhRE44IB64DEY1NLfJQtzWZ0IgYURqLtyXbfax9uTn0renWxJvpOspNUj2/r27kOTKtxGW/NZvuazfbW9WW+2td/T9DVj2tusEyBAgAABAgR6IdB1AVjzvy05LXlv8sJkTz9Ud2neU3fujk9G24nDjhrTtGa9fmZmtI0bPzrGawIECBAgQIDAQgt0WQDW3HXnr4q/9yX1+HdS8fegbK+vytWy3Zqfazknne1fU316XldB91fJlUnT6p+Iq0e89S+RbGo6s6xvE9c/Tff1pI5HI0CAAAECBAj0UqDLzwC+PqJbktuSKtBem4y2C9PxuWFn/Vu/9ePNZydnJU27OCt1F/H05LPJ/0o2JM9N6lvAP5O02815UXP9UVL/8sd7knrkXOPrfS9MaoxGgAABAgQIEOilQJcF4NFD0ftn+ZoldLemvykAlxiyu/sl+fMLSS3/r6SKyr9Iat723b+83N3elT9vSOrn8rck1aoYPDWpH4/WCBAgQIAAAQK9FeiyANwS1cpK21kZWBnX6g7e7wwzbvu4vg+ls6IRIECAAAECBAi0BLr8DGBrN1YJECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYkoACcEbTdECBAgAABAgTmRUABOC9XwnEQIECAAAECBGYk0HUBeErO4/eTTye3J3clW5I9aVszuN43KU8emXDS2FeNjPWSAAECBAgQINArgf07PttzMv9DkhuSa4brWexRe1NGHzbmHQ9K30uTm5NPjdn+lfSdP6b/sjF9uggQIECAAAECvRHougA8PZJXJVWM1Z23c5M9bVUAjmuvGHa+K8sdYwZsTd9ZY/p1ESBAgAABAgR6LdB1AfiRDnV/ejj32zvch6kJECBAgAABAgsn0HUB2BXY92fihyf12cLPL7GTemx8enJE8rXkkqTuRmoECBAgQIAAgV4LrNUCsLn797YJV+97su281vb6YsgFyUuSb7X6l1zdsWPck+Ulh9tAgACBewTuuOOO3eu19HfJPSxWCBDYA4H169fvweg9G7oWC8D75xSfk1QR9+4lTvc30v++pO74VeH36ORXk/pWcp3z85Nl2/bt2we7du1adpwBBAgQGBW46aabdnfVctu2baObvSZAgMBEgXXr1g02b948ccy+bFyLBeBzc8JVBP5hcssSJ/8LI/0X5/XTk3pc/LzknOSKZGLbuHHjxO02EiBAYCmB66+/fvemww8/fLBp06alhuknQIDAqgisxQLw9KHUpMe/4zCbO4avy8bjk2ULwC5vvY47QH0ECCyOwAEHHLD7ZGrp75LFua7OhMCiCHT9Q9DTdnpEJnxi8qXksr2Y/Ibhe+63F+/1FgIECBAgQIDAQgistQKw+fLH3v70yxOGV23rQlw9J0GAAAECBAgQ2AuBeSoAj8rxH5scusR51POUFyb11bp3LjGmuusLH+Pu8J2c/vryR90F7PL3CTO9RoAAAQIECBCYX4GuPwNYn9d70vD0HzVcVt8Jw/ULs6xUq38l5NTktOT8ZLT9aDoenPx5cvenq0dH3P36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CBAgQIAAAQIECBAgQIAAAQIECBAgQIBAHwVOyUn/fvLp5PakPkO8JdEIECBAgAABAgQWVGBrzquKvq8lzfqWrGsECBCYKwE/AzNXl8PBECCwxgVOz/EfnTw4eUuiESBAYC4F/FNwc3lZHBQBAmtU4CNr9LgdNgECPRNwB7BnF9zpEiBAgAABAgQUgP4bIECAAAECBAj0TEAB2LML7nQJECBAgAABAgpA/w0QIECAAAECBHomoADs2QV3ugQIECBAgAABBaD/BggQIECAAAECPRNQAPbsgjtdAgQIECBAgIAC0H8DBAgQIECAAIGeCYsm6N8AAAFbSURBVOzXs/N1ugQIEOhSoP4lkCcNd/CoLB+TfDz5h2HfhVlWNAIECBAgQIAAgQUROD/nUf8W8FI5K9s0AgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIrB2B/x/Mb4NuZx/haQAAAABJRU5ErkJggg==" width="640">


# Optional Recommended Analysis

The following are optional challenge queries. These are highly recommended to attempt, but not required for the homework.

Calcualte the rainfall per weather station using the previous year's matching dates.




```python
start_date = "2016-03-24"
end_date = "2016-04-09"

Pre_start_date = stripdate(start_date)
Pre_end_date = stripdate(end_date)
```


```python
#the rainfall per weather station using the previous year's matching dates.
session.query(Measurements.station, func.avg(Measurements.prcp) ).\
        filter(Measurements.date >= Pre_start_date).\
           filter(Measurements.date <= Pre_end_date).\
        group_by(Measurements.station).all()
            
```




    [('USC00511918', 0.0),
     ('USC00513117', 0.09470588235294118),
     ('USC00514830', 0.07750000000000001),
     ('USC00516128', 0.4961538461538462),
     ('USC00517948', 0.01),
     ('USC00519281', 0.15470588235294117),
     ('USC00519397', 0.042352941176470586),
     ('USC00519523', 0.15866666666666665)]




```python
## daily normal 
start_date = "2016-03-24"
end_date = "2016-04-09"
calc_temps(start_date,  end_date).mean(axis = 1)
```




    0    0.722997
    dtype: float64



Create a function called daily_normals that will calculate the daily normals for a specific date. This date string will be in the format %m-%d. Be sure to use all historic tobs that match that date string.

Create a list of dates for your trip in the format %m-%d. Use the daily_normals function to calculate the normals for each date string and append the results to a list.


Load the list of daily normals into a Pandas DataFrame and set the index equal to the date.

Use Pandas to plot an area plot (stacked=False) for the daily normals.



```python
#  daily_normals function: 


def  daily_normals(input_date):
    
    results = session.query(Measurements.date).all()
    all_date = list(np.ravel(results))  

    result = session.query(Measurements.date).filter(Measurements.date.contains(input_date)).group_by(Measurements.date).all()
    specified_dates = list(np.ravel(result))

    result_list = []

    for i in range(len(specified_dates)):
        if specified_dates[i] in all_date:
            result = session.query(func.avg(Measurements.prcp), func.min(Measurements.prcp), func.max(Measurements.prcp)).\
            filter(Measurements.date == specified_dates[i]).all()
            precp = list(np.ravel(result))  
      
        result_list.append(precp)
    
    rainfall_norm = {}
    
    for j in range(len(result_list)):
        rainfall_norm[specified_dates[j]]  =  np.mean(result_list[j])
    return pd.DataFrame.from_dict(rainfall_norm,orient='index')
```


```python
input_date = '04-09'

df = daily_normals(input_date)
```


```python

import numpy as np
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize = (10,5))

x = range(len(ptps))
ax.stackplot(df.index, df[0])

fig.tight_layout()
fig.show()

```


    <IPython.core.display.Javascript object>



<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA+gAAAH0CAYAAACuKActAAAAAXNSR0IArs4c6QAAQABJREFUeAHs3QmcXGWZ6P83dDaQJBCXQMZt4l9FuQooDC4sGb2C+HcZ9Y46jHOFcZlxm/HOjOMyMIKKqONVRx0XROF6B8cNkpDKSggEAoEQCDuBkKU7SSe9Jb2lu5au7vs8nXqTSqeqazvn1Hve83s/n4dTderUOe/7fapJP13vOccYGgIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIIIAAAggggAACCCCAAAIIVBaYUnmTeG4xNjbWMjAw8PLi3k+ZMmW/PB8rXsdjBBBAAAEEEEAAAQQQQACBRAhMkTpxbvFIZ82atVXqxHzxumY+ntrMg4d5bC3OR0dHnwrzGOwbAQQQQAABBBBAAAEEEEAgvgJSN75Ker/FlREc50pH6AcCCCCAAAIIIIAAAggggAACSRagQE9y9hk7AggggAACCCCAAAIIIICAMwIU6M6kgo4ggAACCCCAAAIIIIAAAggkWcDbAr1wQbhY5DadTpvt27cbXdL8ESCv/uTSjoScWgm/luTVr3zqaMipfzklr+TUTwE/RxW3/we7Vjd6W6DLxz1WV2vP5525cKCf/6do0qjIa5PgQzwsOQ0Rt4m7Jq9NxA/p0OQ0JNgm75a8NjkBIRyenIaA6sAuY5ZXp+pGnwt0Bz6adAEBBBBAAAEEEEAAAQQQQACB6gQo0KtzYisEEEAAAQQQQAABBBBAAAEEQhWgQA+Vl50jgAACCCCAAAII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Dix1c0JsFmS+i1jqu1XE1iFotOW1j3OuUk77ac+hSPn7EUpZP86BVEXC18nYktjNkh++B6kI37VUTMq3Gc670MroGvQk2gN9AOm7eQTKm/rvwUjf2WeQbp7pFfBVkJ7i58c4ii2tj5oq5XUW7dEYOQfpgnwxeg/aC62IzkXHoaLmvlqN39VUvuo4d0PKURiHWW1r7qvVmC/1kynNC36J1FfHIM0f1H8XoclIb/IUNffVavRVvf1wK9J4q3nrX9HOSDdP70O7oniejStp7qvV6KshOcqp5hZ6ULceyl/7UCxsozWvhQGNhMB+TuL1NuqlPm9rUDgH6Qfh39lSZflT1m7/tcRGmhhrgqjX8ySt6zXaTkw/OjOQJiCvoIfQqWglVMRqBOkcZhcJTsRoUL0RLUQvo7noIJQy3fm+Az2HAlu1XRPkMtZPcDvuvdEO/9d5rbdpU9yeqHlNxdGW134IVCmn9QLt6SGmjJX9Dqb2LUYPpCoK+CYQcy3Sj6YmuHrT5YtoLIptdxy3oKeR+upT6Cqkp1plrJ/gKuV1H9pzJXoY6catzu1xdD3aE3Vi7qvNOe6NQJb97rf7ztSi/aeKdZzaz/hUZRtf2famdue+2kylTF71wEM31OYjXbBpfvMoughtijox99Vq9NXNSd51SL9FGoM1Hk9Dq6Gy5r7anFP1s94IZFlOZfpqONSnWdF2VwfHMJZl25s6lNqyLM2XUudgnwmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYgAmYwEgm8F+TYwSxPTGCswAAAABJRU5ErkJggg==" width="1000">
