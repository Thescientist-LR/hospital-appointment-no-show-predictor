# Hospital Appointment No-Show Predictor

**Tioluwani Olubowale · Python, pandas, scikit-learn and Tableau**

Can the details known when someone books an appointment help estimate whether they will miss it? Across 110,521 cleaned appointments, 22,314 were missed (20.19%). Booking lead time showed a particularly clear pattern. The missed rate rose from 4.65% for same-day visits to 33.00% for appointments booked at least 31 days ahead. [Try the interactive booking predictor in Google Colab](https://colab.research.google.com/drive/1YvZawthsyyMkwJ0ZhVAMxzekLoXqUd8w#scrollTo=qjmBU7b8EqAs).

| Comparison | Finding |
|---|---|
| Age | Ages 13–17 had the highest missed rate (26.64%). Ages 65 and older had the lowest (15.50%). |
| SMS reminders | For bookings made 31 or more days ahead, 30.20% were missed when an SMS was recorded, compared with 37.53% when none was recorded. This observational comparison cannot establish the effect of sending a reminder. |
| Neighbourhood | Jardim Camburi recorded 1,465 missed appointments, the largest count. Counts show the volume of missed visits and depend on how many appointments each neighbourhood had. |

## Explore the project

| Open | What you can do |
|---|---|
| [Appointment patterns dashboard](https://public.tableau.com/app/profile/tioluwani.olubowale/viz/HospitalAppointmentNo-ShowPredictor/HospitalAppointmentNo-Shows) | Compare attendance by booking lead time and age, and see where the most appointments were missed. |
| [Model performance dashboard](https://public.tableau.com/app/profile/tioluwani.olubowale/viz/HospitalAppointmentNo-ShowPredictor/No-ShowModelPerformance) | Compare the average predicted chance with the observed missed rate in four risk groups. |
| [Packaged Tableau workbook](Hospital%20Appointment%20No-Show%20Predictor.twbx) | Open both dashboards locally with their data extracts. |
| [Analysis notebook](Hospital_Appointment_No_Show_Predictor.ipynb) | Follow the cleaning, charts, model evaluation and interactive predictor. |
| [Appointment patterns data](Appointment_Patterns.csv) | Explore appointment and missed-visit counts by booking characteristics. |
| [Model performance data](Model_Performance.csv) | Compare predicted and observed rates within each risk group. |

## Reproduce the analysis and try the predictor

1. [Open the interactive predictor](https://colab.research.google.com/drive/1YvZawthsyyMkwJ0ZhVAMxzekLoXqUd8w#scrollTo=qjmBU7b8EqAs) and [download the booking CSV](https://raw.githubusercontent.com/Thescientist-LR/hospital-appointment-no-show-predictor/main/KaggleV2-May-2016.csv).
2. In Colab, choose **Runtime → Run all**. When the upload prompt appears, select **KaggleV2-May-2016.csv**.
3. Scroll to **Predict a new appointment** at the end of the notebook. Choose an age group, time from booking to visit, day of visit and appointment neighbourhood.
4. Try **13–17**, **31+ days**, **Tuesday** and **DO QUADRO**. The notebook example estimates a **40.6%** chance of missing this booking. Change just the waiting time to see how the estimate moves.

If the shared notebook asks for access, download the [notebook file](Hospital_Appointment_No_Show_Predictor.ipynb), open Google Colab, and choose **File → Upload notebook**. Then follow steps 2–4.

## How to read the numbers

The missed rate is missed appointments divided by total appointments in the group. The average predicted chance is the mean of the model’s estimates for bookings in that group.

A logistic regression model uses four booking-time inputs. The training set contains 71,369 earlier bookings whose visits had already taken place by the cutoff. Another 16,187 earlier bookings were still pending at the cutoff and were excluded from training. The evaluation covers 22,965 later bookings.

| Predicted risk group | Average predicted chance | Actual missed rate |
|---|---:|---:|
| Under 10% | 4.95% | 4.10% |
| 10% to under 20% | 17.51% | 18.16% |
| 20% to under 30% | 24.89% | 22.32% |
| 30% or higher | 34.25% | 29.61% |

Missed rates rose across all four groups. In the highest group, the model overestimated the observed rate by 4.64 percentage points. These figures describe performance on later appointments in this dataset. A new hospital or time period would need its own evaluation.

## Sources and scope

The source is the [Medical Appointment No Shows dataset on Kaggle](https://www.kaggle.com/datasets/joniarroba/noshowappointments). Each observation is an appointment. The reported patterns describe bookings in this dataset.
