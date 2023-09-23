The four limit cycle datasets are stored in this directory. They contain the radial and angular component in [0,:] and [1,:], respectively. An example code
of how to construct the empirical Poincaré map is given below:

poincare_mapping_interval = 50
data_file = 'saddle_node_limit_cycle_t10000_p500000_1noise001'

polar_coordinates = np.load(data_file + '.npy')
cartesian_coordinates = np.zeros((2,N))
cartesian_coordinates[0,:] = polar_coordinates[0,:] * np.cos(polar_coordinates[1,:])
cartesian_coordinates[1,:] = polar_coordinates[0,:] * np.sin(polar_coordinates[1,:])

poincare_map_entries = np.zeros((2, int(tend)))
poincare_map_entries[0,:] = cartesian_coordinates[0,0::poincare_mapping_interval]
poincare_map_entries[1,:] = cartesian_coordinates[1,0::poincare_mapping_interval]