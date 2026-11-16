# Issue

**Title:** Upgrade Lets-Plot Kotlin API to v. 0.0.22-SNAPSHOT

## Description

## [0.0.22-SNAPSHOT] 
### Added
- facet_grid() 
- coord_fixed()
- labs(), xlab(), ylab()
- lims(), xlim(), ylim()
- as_discrete()
- Geoms:
    - geom_jitter()
    - geom_bin2d(), stat_bin2d()
    - geom_contour(), stat_contour()
    - geom_contourf()
    - geom_density2d(), stat_density2d()
    - geom_density2df()
    - geom_smooth(), stat_smooth()
    - stat_bin()
- Manual scales:
    - scale_fill_manual(), scale_color_manual()
    - scale_size_manual()
    - scale_shape_manual()
    - scale_linetype_manual()
    - scale_alpha_manual()
- Identity scales:
    - scale_color_identity(), scale_fill_identity()
    - scale_shape_identity()
    - scale_linetype_identity()
    - scale_alpha_identity()
    - scale_size_identity()
- Positional scales:
    - scale_x_continuous(), scale_y_continuous()
    - scale_x_discrete(), scale_y_discrete()
- Brewer color scales:
    - scale_color_brewer(), scale_fill_brewer()
- scale_shape()

### Changed
- scale_color_grey(), scale_fill_grey() : arguments `start`, `end` are now in range [0,1] (before was [0,100]).
- Parameter `mapping` (lambda) has been moved to the last position to allow the value to be outside parentheses.
- theme() is now a fluent interface.

### Fixed:
- theme composition wasn't working.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7229b5bde195`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.