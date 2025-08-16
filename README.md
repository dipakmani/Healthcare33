import pandas as pd
import numpy as np
from faker import Faker
import random

fake = Faker()
num_records = 500000
np.random.seed(42)

data = {
    'operation_id': range(1, num_records + 1),
    'patient_id': np.random.randint(1000, 5000, size=num_records),
    'doctor_id': np.random.randint(200, 500, size=num_records),
    'assistant_doctor_id': np.random.randint(200, 500, size=num_records),
    'anesthetist_id': np.random.randint(200, 500, size=num_records),
    'nurse_id': np.random.randint(100, 300, size=num_records),
    'department_id': np.random.randint(1, 20, size=num_records),
    'hospital_id': np.random.randint(1, 10, size=num_records),
    'room_id': np.random.randint(101, 150, size=num_records),
    'unit_id': np.random.randint(1, 5, size=num_records),
    'shift_id': np.random.randint(1, 4, size=num_records),
    'procedure_id': np.random.randint(1000, 1100, size=num_records),
    'equipment_id': np.random.randint(500, 600, size=num_records),
    'anesthesia_type_id': np.random.randint(1, 5, size=num_records),
    'diagnosis_id': np.random.randint(400, 500, size=num_records),
    'insurance_provider_id': np.random.randint(1, 10, size=num_records),
    'billing_category_id': np.random.randint(1, 5, size=num_records),
    'date_id': [fake.date_between(start_date='-3y', end_date='today') for _ in range(num_records)],
    'time_id': [fake.time() for _ in range(num_records)],
    'operation_duration_minutes': np.random.randint(30, 240, size=num_records),
    'anesthesia_duration_minutes': np.random.randint(20, 180, size=num_records),
    'pre_op_prep_time_minutes': np.random.randint(10, 60, size=num_records),
    'post_op_recovery_time_minutes': np.random.randint(30, 180, size=num_records),
    'total_cost': np.round(np.random.uniform(1000, 50000, size=num_records), 2),
    'doctor_fee': np.round(np.random.uniform(500, 10000, size=num_records), 2),
    'nurse_fee': np.round(np.random.uniform(200, 5000, size=num_records), 2),
    'anesthetist_fee': np.round(np.random.uniform(300, 7000, size=num_records), 2),
    'equipment_cost': np.round(np.random.uniform(100, 20000, size=num_records), 2),
    'medicine_cost': np.round(np.random.uniform(50, 5000, size=num_records), 2),
    'room_cost': np.round(np.random.uniform(100, 2000, size=num_records), 2),
    'insurance_covered_amount': np.round(np.random.uniform(0, 30000, size=num_records), 2),
    'patient_paid_amount': np.round(np.random.uniform(0, 20000, size=num_records), 2),
    'complication_count': np.random.randint(0, 5, size=num_records),
    'blood_units_used': np.random.randint(0, 5, size=num_records),
    'transfusion_cost': np.round(np.random.uniform(0, 5000, size=num_records), 2),
    'medication_dosage_total_mg': np.random.randint(50, 5000, size=num_records),
    'surgery_success_flag': np.random.choice([0, 1], size=num_records),
    'readmission_within_30_days_flag': np.random.choice([0, 1], size=num_records),
    'infection_flag': np.random.choice([0, 1], size=num_records),
    'follow_up_required_flag': np.random.choice([0, 1], size=num_records),
    'operation_type': np.random.choice(['Elective', 'Emergency'], size=num_records),
    'operation_status': np.random.choice(['Scheduled', 'Completed', 'Cancelled', 'Postponed'], size=num_records),
    'anesthesia_type': np.random.choice(['General', 'Local', 'Regional', 'Sedation'], size=num_records),
    'patient_condition_pre_op': np.random.choice(['Stable', 'Critical', 'Serious'], size=num_records),
    'patient_condition_post_op': np.random.choice(['Stable', 'Critical', 'Serious'], size=num_records),
    'surgical_approach': np.random.choice(['Open', 'Laparoscopic', 'Robotic'], size=num_records),
    'operating_team_size_category': np.random.choice(['Small', 'Medium', 'Large'], size=num_records),
    'equipment_status_used': np.random.choice(['Functional', 'Maintenance', 'Backup'], size=num_records),
    'operation_outcome': np.random.choice(['Successful', 'Complication', 'Failure'], size=num_records),
    'data_source': np.random.choice(['EHR_SYSTEM', 'MOBILE_APP', 'FRONT_DESK'], size=num_records),
    'created_at': [fake.date_time_between(start_date='-3y', end_date='now') for _ in range(num_records)],
    'updated_at': [fake.date_time_between(start_date='-3y', end_date='now') for _ in range(num_records)],
}

df = pd.DataFrame(data)
df.to_csv('fact_operations_500k.csv', index=False)
print("CSV file with 5 lakh records created successfully!")
