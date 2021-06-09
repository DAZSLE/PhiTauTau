### Phi(tau tau)

Madgraph setup for generating Phi(tau tau). Instructions:

   - Generate cards with make_cards.py or make_cards_1j.py. The 1j gridpacks are much faster to create, so these are better for debugging. 
   - Checkout genproductions (in 2021, master uses MG 2.6.5). `git clone git@github.com:cms-sw/genproductions`
   - `cd genproductions/bin/MadGraph5_aMCatNLO`
   - Try creating a gridpack:
      - Interactively: genproductions doesn't have an out-of-the-box script, unfortunately, but you can easily make one. Copy the condor script to a new script, e.g. `cp submit_condor_gridpack_generation.sh submit_interactive_gridpack_generation.sh`, and change "condor" to "interactive" in the script. Alternatively, you can run the last line of this script directly. 
      - Using HTCondor: `source submit_condor_gridpack_generation.sh Spin0ToTauTau_1j_scalar_g1_HT300_M100 ../../../cards/scalar_m100/` (args 3 and 4 are SCRAM_ARCH and the CMSSW version, which should be left blank to use the defaults). 

Notes: 
   - CMS stores UFO files at `/afs/cern.ch/cms/generators/www/DMsimp*`
      - Phi(bb) used DMsimp_s_spin0_4f. This appears to be an outdated alpha version... it doesn't work with MG >= 2.6.1, and it doesn't work with HTCondor. It's probably better to use DMsimp_s_spin0.
   - The recommended version of Madgraph is 2.6.5. Newer versions haven't been validated by GEN yet. 
