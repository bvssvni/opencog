
# The atom_types.h file is written to the build directory
INCLUDE_DIRECTORIES(${CMAKE_BINARY_DIR})

# The build order used here is loosely in terms of 
# dependencies: the later parts depend on, or may
# someday depend on the earlier parts.
#
ADD_SUBDIRECTORY (learning)

IF (HAVE_ATOMSPACE)
    ADD_SUBDIRECTORY (nlp)
    ADD_SUBDIRECTORY (persist)
ENDIF (HAVE_ATOMSPACE)

IF (HAVE_SERVER)
    ADD_SUBDIRECTORY (dynamics)
    ADD_SUBDIRECTORY (modules)
    ADD_SUBDIRECTORY (server)
ENDIF(HAVE_SERVER)

# Extension language support
IF (HAVE_ATOMSPACE AND HAVE_GUILE)
	ADD_SUBDIRECTORY (scm)
	ADD_SUBDIRECTORY (shell)
ENDIF (HAVE_ATOMSPACE AND HAVE_GUILE)

IF (HAVE_CYTHON)
	ADD_SUBDIRECTORY (cython)
ENDIF (HAVE_CYTHON)

IF (HAVE_GHC)
	ADD_SUBDIRECTORY (haskell)
ENDIF (HAVE_GHC)

IF (HAVE_SERVER)
    ADD_SUBDIRECTORY (spacetime)
    ADD_SUBDIRECTORY (spatial)
ENDIF (HAVE_SERVER)

# build unconditionally; a check is made there.
ADD_SUBDIRECTORY (embodiment)

# Graphics and visualization subsystems
ADD_SUBDIRECTORY (visualization)
