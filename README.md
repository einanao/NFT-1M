# NFT-1M

[Link to torrent](https://raw.githubusercontent.com/einanao/NFT-1M/main/NFT-1M.torrent), which contains
 - `img.tar.gz` (84GB compressed, 88GB uncompressed)
 - `metadata.tar.gz` (390MB compressed, 6.1GB uncompressed)

A dataset containing 1,359,385 Ethereum NFT images and their metadata.

 - Since multiple NFTs can be minted for the same image, there are only 1,116,157 unique images.
 - Images were first downscaled such that their maximum width or height is 256px, then converted to RGBA and saved as PNGs.
 - Each NFT is characterized by a unique (contract address, token ID) pair. The directories are structured as {img|metadata}/contract_address/token_id.{png|json}.
 - Contract addresses in the dataset roughly correspond to the top 100 collections by market capitalization as of March 2022.
 - Not all token IDs are included for a given contract address (some link to an animation instead of an image, some contain dead links, etc.)
 - NFTs that do not link to images were ignored. This includes NFTs that link to an animation but not an image. We did include NFTs that link to both an animation and an image.
 - All data was downloaded between March and June 2022.
 - You can view NFT details on the web (e.g., to verify the accuracy of the image and metadata for a given token) using Etherscan (`https://etherscan.io/nft/contract_address/token_id`) or OpenSea (`https://opensea.io/assets/contract_address/token_id`).
 - **Warning**: some images may be NSFW

## Generative model of NFT images

 - [Link to pre-trained StyleGAN2 model](https://www.dropbox.com/sh/0hom65me1qxzcst/AAAkilf4tw1pIXoVIm62uqn5a?dl=0) (999MB)

Includes model checkpoints and samples generated using lucidrains' [stylegan2-pytorch](https://github.com/lucidrains/stylegan2-pytorch/tree/e7cbe0381f577f3a55ffb04bc29cbb1feb479f0c) code and command
`stylegan2_pytorch --data img --multi-gpus --batch-size 32 --gradient-accumulate-every 1 --transparent`.

Below are some NFTs that do not exist.

<img src="https://raw.githubusercontent.com/einanao/NFT-1M/main/stylegan2-samples.png" width="450" height="auto">

I will continue training the model and periodically uploading checkpoints as long as I can, or until the losses diverge.

## Copyright

The NFT images in the dataset probably all have their own individual copyright details specified somewhere on the web, so I don't make any claims about those. For the pre-trained StyleGAN2 model, I release any copyright I may have to all generated images under the [CC-0](https://creativecommons.org/share-your-work/public-domain/cc0/) (public domain equivalent) license.
