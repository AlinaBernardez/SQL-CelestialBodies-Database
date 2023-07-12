# SQL-CelestialBodies-Database

--
-- PostgreSQL database dump
--

-- Dumped from database version 12.9 (Ubuntu 12.9-2.pgdg20.04+1)
-- Dumped by pg_dump version 12.9 (Ubuntu 12.9-2.pgdg20.04+1)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

DROP DATABASE universe;
--
-- Name: universe; Type: DATABASE; Schema: -; Owner: freecodecamp
--

CREATE DATABASE universe WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'C.UTF-8' LC_CTYPE = 'C.UTF-8';


ALTER DATABASE universe OWNER TO freecodecamp;

\connect universe

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: dwarf_planets; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.dwarf_planets (
    dwarf_planets_id integer NOT NULL,
    name character varying(30) NOT NULL,
    discovery_year integer,
    has_life boolean
);


ALTER TABLE public.dwarf_planets OWNER TO freecodecamp;

--
-- Name: galaxy; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.galaxy (
    galaxy_id integer NOT NULL,
    name character varying(30) NOT NULL,
    type text,
    distance_earth_mly numeric(4,3),
    absolute_size numeric
);


ALTER TABLE public.galaxy OWNER TO freecodecamp;

--
-- Name: moon; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.moon (
    moon_id integer NOT NULL,
    name character varying(30) NOT NULL,
    discovery_year integer,
    distance_earth_km numeric,
    planet_id integer
);


ALTER TABLE public.moon OWNER TO freecodecamp;

--
-- Name: planet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet (
    planet_id integer NOT NULL,
    name character varying(30) NOT NULL,
    has_life boolean,
    rotation_days integer,
    star_id integer
);


ALTER TABLE public.planet OWNER TO freecodecamp;

--
-- Name: star; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.star (
    star_id integer NOT NULL,
    name character varying(30),
    constellation character varying(30),
    distance_from_earth integer,
    galaxy_id integer NOT NULL
);


ALTER TABLE public.star OWNER TO freecodecamp;

--
-- Data for Name: dwarf_planets; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.dwarf_planets VALUES (2, 'Pluto', 1930, NULL);
INSERT INTO public.dwarf_planets VALUES (3, 'Quaoar', 2002, NULL);
INSERT INTO public.dwarf_planets VALUES (4, 'Sedna', 2003, NULL);
INSERT INTO public.dwarf_planets VALUES (5, 'Orcus', 2004, NULL);
INSERT INTO public.dwarf_planets VALUES (6, 'Haumea', 2004, NULL);
INSERT INTO public.dwarf_planets VALUES (1, 'Ceres', 1801, false);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.galaxy VALUES (1, 'Milky Way', 'SBcC', 0.026, 20.8);
INSERT INTO public.galaxy VALUES (2, 'Segue I', 'dSph', 0.075, 3);
INSERT INTO public.galaxy VALUES (3, 'Large MAgellanic Cloud', 'SBm', 0.163, 17.93);
INSERT INTO public.galaxy VALUES (4, 'Draco Dwarf', 'SH pec', 0.258, 8.74);
INSERT INTO public.galaxy VALUES (5, 'Carina Dwarf', 'dE3', 0.330, 8.97);
INSERT INTO public.galaxy VALUES (6, 'Andromeda II', 'dE0', 2.220, 12.6);


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.moon VALUES (1, 'Moon', 0, 3476, 1);
INSERT INTO public.moon VALUES (2, 'Deimos', 1877, 2430, 4);
INSERT INTO public.moon VALUES (3, 'Phobos', 1877, 9200, 4);
INSERT INTO public.moon VALUES (4, 'Adrastea', 1979, 123000, 5);
INSERT INTO public.moon VALUES (5, 'Aoede', 2033, 23800000, 5);
INSERT INTO public.moon VALUES (6, 'Carme', 1939, 22600000, 5);
INSERT INTO public.moon VALUES (7, 'Elara', 1905, 11000000, 5);
INSERT INTO public.moon VALUES (8, 'Io', 1610, 421000, 5);
INSERT INTO public.moon VALUES (9, 'Metis', 1979, 127000, 5);
INSERT INTO public.moon VALUES (10, 'Sponde', 2001, 23000000, 5);
INSERT INTO public.moon VALUES (11, 'Aegir', 2005, 20000000, 6);
INSERT INTO public.moon VALUES (12, 'Bestla', 2005, 20000000, 6);
INSERT INTO public.moon VALUES (13, 'Fenrir', 2005, 22000000, 6);
INSERT INTO public.moon VALUES (14, 'Hati', 2005, 19000000, 6);
INSERT INTO public.moon VALUES (15, 'Pan', 1990, 123000, 6);
INSERT INTO public.moon VALUES (16, 'Skoll', 2006, 17000000, 6);
INSERT INTO public.moon VALUES (17, 'Titan', 1655, 1200000, 6);
INSERT INTO public.moon VALUES (18, 'Ariel', 1851, 191000, 7);
INSERT INTO public.moon VALUES (19, 'Cupid', 2003, 77000, 7);
INSERT INTO public.moon VALUES (20, 'Titania', 1787, 435000, 7);


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet VALUES (1, 'Earth', true, 1, 13);
INSERT INTO public.planet VALUES (2, 'Mercury', false, 58, 13);
INSERT INTO public.planet VALUES (3, 'Venus', false, -243, 13);
INSERT INTO public.planet VALUES (4, 'Mars', true, 1, 13);
INSERT INTO public.planet VALUES (5, 'Jupiter', false, 1, 13);
INSERT INTO public.planet VALUES (6, 'Saturn', false, 1, 13);
INSERT INTO public.planet VALUES (7, 'Uranus', false, 1, 13);
INSERT INTO public.planet VALUES (8, 'Neptune', false, 1, 13);
INSERT INTO public.planet VALUES (9, 'Ceres', false, 1, 13);
INSERT INTO public.planet VALUES (10, 'Pluton', false, 1, 13);
INSERT INTO public.planet VALUES (11, 'Eris', false, 1, 13);
INSERT INTO public.planet VALUES (12, 'Makemake', false, 1, 13);


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.star VALUES (1, 'Altair', 'Aquila', 16, 1);
INSERT INTO public.star VALUES (2, 'Hamal', 'Aries', 66, 1);
INSERT INTO public.star VALUES (3, 'Gamma Cassiopeiae', 'Cassiopea', 615, 1);
INSERT INTO public.star VALUES (4, 'Alpha Doradus', 'Dorado', 176, 1);
INSERT INTO public.star VALUES (5, 'Alpha Indi', 'Indus', 101, 1);
INSERT INTO public.star VALUES (6, 'Peacock', 'Pavo', 183, 1);
INSERT INTO public.star VALUES (7, 'Enif', 'Pegasus', 670, 1);
INSERT INTO public.star VALUES (8, 'Naos', 'Puppis', 1400, 1);
INSERT INTO public.star VALUES (9, 'Polaris', 'Ursa menor', 430, 1);
INSERT INTO public.star VALUES (10, 'Spica', 'Virgo', 26, 1);
INSERT INTO public.star VALUES (11, 'Alioth', 'Ursa major', 81, 1);
INSERT INTO public.star VALUES (12, 'Aldebaran', 'Taurus', 65, 1);
INSERT INTO public.star VALUES (13, 'Sun', 'Sistema Solar', 1, 1);


--
-- Name: dwarf_planets dwarf_planets_dwarf_id_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.dwarf_planets
    ADD CONSTRAINT dwarf_planets_dwarf_id_key UNIQUE (dwarf_planets_id);


--
-- Name: dwarf_planets dwarf_planets_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.dwarf_planets
    ADD CONSTRAINT dwarf_planets_pkey PRIMARY KEY (dwarf_planets_id);


--
-- Name: galaxy galaxy_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name_key UNIQUE (name);


--
-- Name: galaxy galaxy_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);


--
-- Name: moon moon_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name_key UNIQUE (name);


--
-- Name: moon moon_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);


--
-- Name: planet planet_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name_key UNIQUE (name);


--
-- Name: planet planet_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);


--
-- Name: star star_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name_key UNIQUE (name);


--
-- Name: star star_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);


--
-- Name: moon moon_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: planet planet_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: star star_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--

