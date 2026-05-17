[https://roadmap.sh/projects/pharmaceutical-sales-data](https://roadmap.sh/projects/pharmaceutical-sales-data)
# Pharma-Sales-Data
#1
import pandas as pd
df = pd.read_csv('salesdaily.csv')

cols = ['M01AB','M01AE','N02BE','N05B','N05C','R03','R06']
totals = df[cols].sum()
print(totals)


    print("-" * 35)
    for rank, (drug, val) in enumerate(top3.items(), 1):
        print(f"  {rank}. {drug:8s}  {val:>10,.2f}")

#2
import pandas as pd
df = pd.read_csv('salesdaily.csv')

cols = ['M01AB','M01AE','N02BE','N05B','N05C','R03','R06']
totals = df[cols].sum()
max_cols = totals.idxmax()
max_vals = totals.max()
print(max_cols, max_vals)

#3
import pandas as pd
df = pd.read_csv('salesdaily.csv')

df['datum'] = pd.to_datetime(df['datum'])

periods = [
    (2015, 1,  'January 2558'),
    (2016, 7,  'July 2559'),
    (2017, 9,  'September 2560'),
]

cols = ['M01AB','M01AE','N02BA','N02BE','N05B','N05C','R03','R06']

for year, month, label in periods:
    mask = (df['datum'].dt.year == year) & (df['datum'].dt.month == month)
    filtered = df[mask][cols].sum()
    
    top3 = filtered.sort_values(ascending=False).head(3)
    
    print(f"/n {label}")
    print("-" * 35)
    for rank, (drug, val) in enumerate(top3.items(), 1):
        print(f"  {rank}. {drug:8s}  {val:>10,.2f}")


#4
import pandas as pd
df = pd.read_csv('salesdaily.csv')

df['datum'] = pd.to_datetime(df['datum'])

cols = ['M01AB','M01AE','N02BA','N02BE','N05B','N05C','R03','R06']

df_2017 = df[df['datum'].dt.year == 2017]
totals_2017 = df_2017[cols].sum()

best = totals_2017.idxmax()
best_val = totals_2017.max()

print(f"Best in 2017: {best} ({best_val:,.2f})")


#5
import pandas as pd
df = pd.read_csv('salesdaily.csv')

cols = ['M01AB','M01AE','N02BA','N02BE','N05B','N05C','R03','R06']
avg_per_day = df[cols].mean()

best_cols = avg_per_day.idxmax()
best_val = avg_per_day.max()

print(f"Average per day : {best_cols} ({best_val:,.2f})")


#6
import pandas as pd
df = pd.read_csv('salesdaily.csv')
df['datum'] = pd.to_datetime(df['datum'])

monthly = df.groupby(df['datum'].dt.month)['R03'].mean()
overall_avg = monthly.mean()

high_months = monthly[monthly > overall_avg]
best_month = monthly.idxmax()

if not high_months.empty:
    print(f"month of R03 higher average ({overall_avg:.2f})")
    print(f"   Best month: Month {best_month} ({monthly[best_month]:.2f})")
else:
    print("No R03 higher")




