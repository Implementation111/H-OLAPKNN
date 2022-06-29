## RegionalSales:

Source: https://data.world/dataman-udit/us-regional-sales-data

Hierarchies:

H_cus_geo = Hierarchy("H_cus_geo", ['customer_id', 'postal_code','state','country','region'],{'customer_id':{'customer_name'}, 'postal_code':{'city'}, 'state':{'state_population'}})
H_cus_seg = Hierarchy("H_cus_seg", ['customer_id', 'segment'],{'customer_id':{'customer_name'}})
H_prod_cat = Hierarchy("H_prod_cat", ['product_id', 'sub_category','category'],{'product_id':{'product_name'}})

Dimensions:
D_customers = Dimension("SUPERSTORE_CUsTOMER", ['customer_id', 'postal_code','state','country','region', 'customer_name', 'city', 'state_population'], 'customer_id', {H_cus_geo, H_cus_seg})

#tuples: 793


D_products = Dimension("SUPERSTORE_PRODUCT", ['product_id', 'sub_category','category', 'product_name'], 'project_id', {H_prod_cat})

#tuples: 1204

## IBRD:

Source: https://cubes.readthedocs.io/en/v1.0.1/_downloads/IBRD_Balance_Sheet__FY2010.csv

Hierarchies:
H_item = Hierarchy("H_item", ['line_item', 'subcategory_code','subcategory', 'category_code', 'category'],{'subcategory_code':{'subcategory'}, 'category_code':{'category'}})

Dimensions:
D_item = Dimension("items", ['line_item', 'subcategory_code','subcategory', 'category_code', 'category'], 'line_item', {H_item})

#tuples: 31

## MIGA:

Source: https://finances.worldbank.org/Projects/MIGA-Issued-Projects/cg7w-bf4s

Hierarchies:
H_geo = Hierarchy("H_geo", ['project_id', 'host_country_code','host_region_code'],{'project_id':{'project_name'}, 'host_country_code':{'host_country'}, 'host_region_code':{'host_region'}})
H_sec = Hierarchy("H_sec", ['project_id', 'business_sector'],{'project_id':{'project_name'}})

Dimensions:
D_projects = Dimension("projects", ['project_id', 'project_name', 'host_country_code', 'host_country', 'host_region_code', 'host_region', 'business_sector'], 'project_id', {H_geo, H_sec})

#tuples: 388
