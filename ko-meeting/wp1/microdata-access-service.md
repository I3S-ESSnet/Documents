# Microdata access (confidentiality on the fly)

**DO**: Statistics Canada

**RO**: Istat

**Rank**: 4

**Functionalities mapped to the GSBPM**: 6.4 Apply disclosure control

**State of achievement**: Released version 1.0

**Distance to CSPA**: available in CSPA catalogue

**Technical prerequisites**: R, Java

**Risks**: -

**Description**: This service provides basic functionality for configuring confidentiality-on-the-fly (COF) services. Currently, configuration consists of setting scope keys, updating global configuration parameters (name-values pairs) and setting perturbation tables. This service may be split into two separate services, one scoped around managing scope keys only (per dataset, as in the current implementation, per user or independently) and another service scoped around the configuration parameters and perturbation tables. There is no single perturbation strategy. For example, one may apply perturbations per user, per dataset or some other way. Current implementation of this service assumes that perturbations would be applied per user. For example, datasets being accessed by very trusted partners may require no perturbation, while the same dataset accessed by less trusted partners may require at least some perturbation. Perturbation per dataset strategy would apply the same perturbation per dataset regardless of who accesses it. Istat can build on its experience in this field to set up a solid re-use case of the software developed by StatCan and available on CSPA catalogue. Alternative solutions based on current activities amongst statistical offices will also be studied (for example based on Argus): this could lead to adding a development activity (and thus a DO) to this operation.
