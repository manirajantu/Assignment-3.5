# Introduction to PostgreSQL: Assignment

## Brief

Refer to the ERD (same as lesson).

<img src="./assets/images/car-park-erd.png" />

In the lesson, you have finished:
1. Create drivers table
2. Create vehicles table
3. Create one-to-one relationship between drivers and vehicles.

In this assignment, you will continue to work on:
1. Create car_park table.
2. Create parking_histories table.
3. Create foreign keys to associate:
    - one car_park has zero to many parking_histories
    - one vehicle has zero to many parking-histories

Demonstrate your understanding by inserting SQL Queries related to table creation and foreign key creation below.

You may use `pg_dump` to export your database and include the file in this repository.


```sql


PGDMP     &    8                z            postgres    14.2    14.1 $               0    0    ENCODING    ENCODING        SET client_encoding = 'UTF8';
                      false                       0    0 
   STDSTRINGS 
   STDSTRINGS     (   SET standard_conforming_strings = 'on';
                      false                       0    0 
   SEARCHPATH 
   SEARCHPATH     8   SELECT pg_catalog.set_config('search_path', '', false);
                      false                       1262    14023    postgres    DATABASE     ]   CREATE DATABASE postgres WITH TEMPLATE = template0 ENCODING = 'UTF8' LOCALE = 'en_US.UTF-8';
    DROP DATABASE postgres;
                postgres    false                        0    0    DATABASE postgres    COMMENT     N   COMMENT ON DATABASE postgres IS 'default administrative connection database';
                   postgres    false    3615            ÿ            1259    16422    car_park    TABLE     ñ   CREATE TABLE public.car_park (
    id integer NOT NULL,
    address character varying(50) NOT NULL,
    no_of_slots character varying(20) NOT NULL
);
    DROP TABLE public.car_park;
       public         heap    Enjodi    false            ◊            1259    16421    car_park_id_seq    SEQUENCE     á   CREATE SEQUENCE public.car_park_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 &   DROP SEQUENCE public.car_park_id_seq;
       public          Enjodi    false    216            !           0    0    car_park_id_seq    SEQUENCE OWNED BY     C   ALTER SEQUENCE public.car_park_id_seq OWNED BY public.car_park.id;
          public          Enjodi    false    215            ‘            1259    16398    drivers    TABLE     õ   CREATE TABLE public.drivers (
    id integer NOT NULL,
    car_license_no character varying(20) NOT NULL,
    full_name character varying(100) NOT NULL
);
    DROP TABLE public.drivers;
       public         heap    Enjodi    false            ”            1259    16397    drivers_id_seq    SEQUENCE     Ü   CREATE SEQUENCE public.drivers_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 %   DROP SEQUENCE public.drivers_id_seq;
       public          Enjodi    false    212            "           0    0    drivers_id_seq    SEQUENCE OWNED BY     A   ALTER SEQUENCE public.drivers_id_seq OWNED BY public.drivers.id;
          public          Enjodi    false    211            ÷            1259    16410    parking_histories    TABLE     †   CREATE TABLE public.parking_histories (
    id integer NOT NULL,
    slot_no character varying(20) NOT NULL,
    vehicle_id integer,
    car_park_id integer
);
 %   DROP TABLE public.parking_histories;
       public         heap    Enjodi    false            ’            1259    16409    parking_histories_id_seq    SEQUENCE     ê   CREATE SEQUENCE public.parking_histories_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 /   DROP SEQUENCE public.parking_histories_id_seq;
       public          Enjodi    false    214            #           0    0    parking_histories_id_seq    SEQUENCE OWNED BY     U   ALTER SEQUENCE public.parking_histories_id_seq OWNED BY public.parking_histories.id;
          public          Enjodi    false    213            “            1259    16391    vehicles    TABLE     ´   CREATE TABLE public.vehicles (
    id integer NOT NULL,
    type character varying(50) NOT NULL,
    car_plate_no character varying(10) NOT NULL,
    driver_id integer
);
    DROP TABLE public.vehicles;
       public         heap    Enjodi    false            —            1259    16390    vehicles_id_seq    SEQUENCE     á   CREATE SEQUENCE public.vehicles_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 &   DROP SEQUENCE public.vehicles_id_seq;
       public          Enjodi    false    210            $           0    0    vehicles_id_seq    SEQUENCE OWNED BY     C   ALTER SEQUENCE public.vehicles_id_seq OWNED BY public.vehicles.id;
          public          Enjodi    false    209            {
           2604    16425    car_park id    DEFAULT     j   ALTER TABLE ONLY public.car_park ALTER COLUMN id SET DEFAULT nextval('public.car_park_id_seq'::regclass);
 :   ALTER TABLE public.car_park ALTER COLUMN id DROP DEFAULT;
       public          Enjodi    false    216    215    216            y
           2604    16401 
   drivers id    DEFAULT     h   ALTER TABLE ONLY public.drivers ALTER COLUMN id SET DEFAULT nextval('public.drivers_id_seq'::regclass);
 9   ALTER TABLE public.drivers ALTER COLUMN id DROP DEFAULT;
       public          Enjodi    false    211    212    212            z
           2604    16413    parking_histories id    DEFAULT     |   ALTER TABLE ONLY public.parking_histories ALTER COLUMN id SET DEFAULT nextval('public.parking_histories_id_seq'::regclass);
 C   ALTER TABLE public.parking_histories ALTER COLUMN id DROP DEFAULT;
       public          Enjodi    false    213    214    214            x
           2604    16394    vehicles id    DEFAULT     j   ALTER TABLE ONLY public.vehicles ALTER COLUMN id SET DEFAULT nextval('public.vehicles_id_seq'::regclass);
 :   ALTER TABLE public.vehicles ALTER COLUMN id DROP DEFAULT;
       public          Enjodi    false    210    209    210                      0    16422    car_park 
   TABLE DATA           <   COPY public.car_park (id, address, no_of_slots) FROM stdin;
    public          Enjodi    false    216   £&                 0    16398    drivers 
   TABLE DATA           @   COPY public.drivers (id, car_license_no, full_name) FROM stdin;
    public          Enjodi    false    212   Ò&                 0    16410    parking_histories 
   TABLE DATA           Q   COPY public.parking_histories (id, slot_no, vehicle_id, car_park_id) FROM stdin;
    public          Enjodi    false    214   *'                 0    16391    vehicles 
   TABLE DATA           E   COPY public.vehicles (id, type, car_plate_no, driver_id) FROM stdin;
    public          Enjodi    false    210   ]'       %           0    0    car_park_id_seq    SEQUENCE SET     =   SELECT pg_catalog.setval('public.car_park_id_seq', 3, true);
          public          Enjodi    false    215            &           0    0    drivers_id_seq    SEQUENCE SET     <   SELECT pg_catalog.setval('public.drivers_id_seq', 2, true);
          public          Enjodi    false    211            '           0    0    parking_histories_id_seq    SEQUENCE SET     F   SELECT pg_catalog.setval('public.parking_histories_id_seq', 3, true);
          public          Enjodi    false    213            (           0    0    vehicles_id_seq    SEQUENCE SET     =   SELECT pg_catalog.setval('public.vehicles_id_seq', 3, true);
          public          Enjodi    false    209            É
           2606    16427    car_park car_park_pkey 
   CONSTRAINT     T   ALTER TABLE ONLY public.car_park
    ADD CONSTRAINT car_park_pkey PRIMARY KEY (id);
 @   ALTER TABLE ONLY public.car_park DROP CONSTRAINT car_park_pkey;
       public            Enjodi    false    216            
           2606    16403    drivers drivers_pkey 
   CONSTRAINT     R   ALTER TABLE ONLY public.drivers
    ADD CONSTRAINT drivers_pkey PRIMARY KEY (id);
 >   ALTER TABLE ONLY public.drivers DROP CONSTRAINT drivers_pkey;
       public            Enjodi    false    212            Å
           2606    16415 (   parking_histories parking_histories_pkey 
   CONSTRAINT     f   ALTER TABLE ONLY public.parking_histories
    ADD CONSTRAINT parking_histories_pkey PRIMARY KEY (id);
 R   ALTER TABLE ONLY public.parking_histories DROP CONSTRAINT parking_histories_pkey;
       public            Enjodi    false    214            }
           2606    16396    vehicles vehicles_pkey 
   CONSTRAINT     T   ALTER TABLE ONLY public.vehicles
    ADD CONSTRAINT vehicles_pkey PRIMARY KEY (id);
 @   ALTER TABLE ONLY public.vehicles DROP CONSTRAINT vehicles_pkey;
       public            Enjodi    false    210            Ñ
           2606    16404    vehicles fk_driver_id 
   FK CONSTRAINT     x   ALTER TABLE ONLY public.vehicles
    ADD CONSTRAINT fk_driver_id FOREIGN KEY (driver_id) REFERENCES public.drivers(id);
 ?   ALTER TABLE ONLY public.vehicles DROP CONSTRAINT fk_driver_id;
       public          Enjodi    false    212    210    3455            Ü
           2606    16428 &   parking_histories fk_parking_histories 
   FK CONSTRAINT     å   ALTER TABLE ONLY public.parking_histories
    ADD CONSTRAINT fk_parking_histories FOREIGN KEY (car_park_id) REFERENCES public.car_park(id);
 P   ALTER TABLE ONLY public.parking_histories DROP CONSTRAINT fk_parking_histories;
       public          Enjodi    false    214    216    3459            Ö
           2606    16416    parking_histories fk_vehicle_id 
   FK CONSTRAINT     Ñ   ALTER TABLE ONLY public.parking_histories
    ADD CONSTRAINT fk_vehicle_id FOREIGN KEY (vehicle_id) REFERENCES public.vehicles(id);
 I   ALTER TABLE ONLY public.parking_histories DROP CONSTRAINT fk_vehicle_id;
       public          Enjodi    false    214    210    3453               >   xú3‰LŒHÃKœå/ OL·4Â2‚,œœO…IÃK)éO) ,KÂ4‚2ÊNÕMJ,™„¥‡ä—„‚‚ Ô<z         )   xú3‰442vtrÊÙM,™‰2‚46153O MÚÛ2πbÙ∏∏∏ è⁄˘         #   xú3‰42‰B.#Œ$#N ‰2Ê46‡\1z\\\ Gø4         ?   xú3ÊÙ…/*™‰ˆı5671	ÂåÒ„2‰)*MŒÊˆp4666å‚4‰2Ç*3426q‰4‚ä—„‚‚ ‘√     

=========== End of SQL ====================


postgres=# \d drivers;
                                        Table "public.drivers"
     Column     |          Type          | Collation | Nullable |               Default               
----------------+------------------------+-----------+----------+-------------------------------------
 id             | integer                |           | not null | nextval('drivers_id_seq'::regclass)
 car_license_no | character varying(20)  |           | not null | 
 full_name      | character varying(100) |           | not null | 
Indexes:
    "drivers_pkey" PRIMARY KEY, btree (id)
Referenced by:
    TABLE "vehicles" CONSTRAINT "fk_driver_id" FOREIGN KEY (driver_id) REFERENCES drivers(id)

(END)


postgres=# \d vehicles;
                                      Table "public.vehicles"
    Column    |         Type          | Collation | Nullable |               Default                
--------------+-----------------------+-----------+----------+--------------------------------------
 id           | integer               |           | not null | nextval('vehicles_id_seq'::regclass)
 type         | character varying(50) |           | not null | 
 car_plate_no | character varying(10) |           | not null | 
 driver_id    | integer               |           |          | 
Indexes:
    "vehicles_pkey" PRIMARY KEY, btree (id)
Foreign-key constraints:
    "fk_driver_id" FOREIGN KEY (driver_id) REFERENCES drivers(id)
Referenced by:
    TABLE "parking_histories" CONSTRAINT "fk_vehicle_id" FOREIGN KEY (vehicle_id) REFERENCES vehicles(id)

postgres=# 

postgres=# \d parking_histories;
                                      Table "public.parking_histories"
   Column    |         Type          | Collation | Nullable |                    Default                    
-------------+-----------------------+-----------+----------+-----------------------------------------------
 id          | integer               |           | not null | nextval('parking_histories_id_seq'::regclass)
 slot_no     | character varying(20) |           | not null | 
 vehicle_id  | integer               |           |          | 
 car_park_id | integer               |           |          | 
Indexes:
    "parking_histories_pkey" PRIMARY KEY, btree (id)
Foreign-key constraints:
    "fk_parking_histories" FOREIGN KEY (car_park_id) REFERENCES car_park(id)
    "fk_vehicle_id" FOREIGN KEY (vehicle_id) REFERENCES vehicles(id)
:


postgres-# \d car_park;
                                      Table "public.car_park"
   Column    |         Type          | Collation | Nullable |               Default                
-------------+-----------------------+-----------+----------+--------------------------------------
 id          | integer               |           | not null | nextval('car_park_id_seq'::regclass)
 address     | character varying(50) |           | not null | 
 no_of_slots | character varying(20) |           | not null | 
Indexes:
    "car_park_pkey" PRIMARY KEY, btree (id)
Referenced by:
    TABLE "parking_histories" CONSTRAINT "fk_parking_histories" FOREIGN KEY (car_park_id) REFERENCES car_park(id)

postgres-# 










```

## Submission Guidelines

- Cite any relevant sources consulted during your research
- Solve the problems using your own code
- Do not copy and paste solutions from the source material
- Submit your assignment to black board.
