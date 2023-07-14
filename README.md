# BRC721Auto
|  -   | -  |
|  ----  | ----  |
| Name  | BRC721Auto |
| Description  | Fully Autonomous Generative Art Protocol on Bitcoin |
| Discussion-to | [https://bitcointalk.org/index.php?topic=5459410] |
| Category | Ordinals |


## Abstract
We propose a new standard for Ordinal NFTs, which leverages Recursive Inscription to cost-effectively create fully on-chain generative art that is not controlled by anyone.

## Motivation
Generative art refers to artworks entirely created by autonomous systems.

Fully on-chain generative art needs to satisfy the following three laws:
- Decentralized storage of the code that automatically generates graphics
- Decentralized execution of code based on user-provided parameters for personalized graphic generation
- Decentralized verification of the correctness of the generated results

Based on this, we can determine that ArtBlock on Ethereum is not fully on-chain generative art. Although its core code is stored on Ethereum, the libraries required for code execution are not on-chain, and the processes of code execution and result verification are both carried out by off-chain tools.

However, with the development of Bitcoin's Recursive Inscription technology, Bitcoin has developed an infrastructure that can execute on-chain code at low cost and complete real-time rendering. This paves the way for fully on-chain generative art, leading to the birth of BRC721Auto. Unless someone launches a 51% attack on Bitcoin, this fully on-chain generative art will be permanently and constantly preserved.

## Specifics
The fully on-chain generative art proposed by BRC721Auto is composed of at least two inscriptions: one is the inscription of the code, and the other is the inscription of personalized parameters.

### Code Inscription

In the Code inscription, we need to encode an algorithm that can automatically generate an HTML DOM based on the content of the parameter `p`. This DOM may be a canvas, an SVG, or other content that can be recognized by the browser and rendered into graphics accordingly. 

Of course, the Code inscription can also reference the content of other inscriptions to complete its algorithm.

```javascript
// other functions

async function start() {
    let parameters = p || {};
    // build HTML DOM
}

start();
```

### Parameter Inscription (NFT)

In the Parameter Inscription, we need to define an HTML, and in it, define a global parameter `p` and reference a Code Inscription. When ordinal browsers try to display this Parameter Inscription, they will recognize the global parameter `p`, and automatically execute the `start()` function in the Code Inscription to add or modify the DOM of the current HTML, and finally render the content of this HTML. 

Therefore, the Parameter Inscription can be regarded as the final NFT (Non-Fungible Token).

```HTML
<!DOCTYPE html>
<html>
  <script>
    let p = { "key": "value" }; 
  </script>
  <script src="/content/[algorithm inscription ID]"></script>
</html>
```

## Rationale

Fully on-chain generative art should be self-contained without relying on any off-chain resources. 

Therefore, in designing ERC721Auto, with the help of Recursive Inscription technology, we have put the code required for generating graphics, the execution process of the code, and the verification process all under the protection of the consensus of the Bitcoin blockchain. Unless someone can launch a 51% attack on Bitcoin, no one can control the generation process of ERC721Auto NFTs, which will be autonomously executed by the Bitcoin ecosystem.

## Backward Compatibility
All generative art produced by ERC721Auto are standard Recursive Inscriptions that can be properly parsed by all ordinal browsers.

## Copyright
Copyright and related rights waived via [MIT](../LICENSE.md).



