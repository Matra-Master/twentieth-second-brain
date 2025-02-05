---
created: 20221130-1740
tags:
  - Resources/mysql
---

SQL Cascades ensures deletion of associated record

When you want to delete some record that has a relationship with others,    
maybe on intermediate tables, you need to "cascade" de delete operation   
to all others in order to avoid having dead or useless data

    AlTER TABLE some_table ADD CONSTRAINT other_table_constraint_id FOREIGN KEY other_table_id
    REFERENCES some_table (id) ON DELETE CASCADE;

The significan part is the end 'ON DELETE CASCADE' that erases the related records without me having to worry about side effects of my deletion

---
# References
