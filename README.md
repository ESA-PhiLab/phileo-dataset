# phileo-dataset
    There are 3 main preprocessing scripts in this GitHub repository:

    1.  preprocess_SAFE2TIF: takes the level 2A S2 files (.SAFE), merges the bands and saves the results as a .tif file.
        In the datafolder this is the step mini_foundation_SAFE --> mini_foundation_tifs

    2.  preprocess TIF2NPY: takes the raster files (.tif) and creates numpy arrays of shape (n_patches, tile_size, tile_size, channels)
        In the process cloudy patches will be discarded. If raster labels are available, numpy arrays of the corresponding labels are created as well.
        if dataset = mini_foundation, this is the step mini_foundation_tifs --> mini_foundation_patches_np
        if dataset = downstream, this is the step downstream_dataset_tifs --> downstream_dataset_patches_np

    3.  preprocess_raster2labels: create raster labels for terrain, encoded coordinates or Koppen-Geiger climate zones.
        labels for images are created by cropping from a global raster. Global rasters are found under aux_data
        Terrain: aux_data/copdem30.vrt
        Koppen-Geiger: aux_data/beck_kg_map_masked.tif
        encoded coordinates: encoded_coordinates_global.tif
        In the datafolder this is the step aux_data --> **label_kg.tif, **label_coords.tif, **label_terrain.tif
