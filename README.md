# SoA

### What is SoA?

***Secrets of Aging*** (SoA) is a grand theory about aging. It consists of a few underlying biological mechanisms, which, when combined and extended, can explain all aging-related fatal diseases, nearly all aging-related non-statistical phenomena, and some aging-related statistical phenomena of humankind and some other animal species. It is believed that the mechanisms are actionable with modern medical sciences.

SoA in this context refers to a text of 1023 characters that briefly outlines the theory.

SoA is custom-encrypted. This package provides everything needed to decrypt it, except the passphrases and alike.

The knowledge in SoA will be disclosed if [the conditions](DisclosureConditions.md) are met. Otherwise, decryption information will be disclosed with the goal that SoA can be decrypted after around 2070.

### File descriptions

#### *cipherdata* directory:

- ***alpha.7z.cipher***: Cipher data of alpha.7z, which contains source code of "Alpha" cipher. Encrypted with alpha-encrypter.
- ***bravo.7z.cipher***: Cipher data of bravo.7z, which contains source code of "Bravo" cipher. Encrypted with bravo-encrypter.
- ***prims1_params2.7z***: Contains 65537 binary files, of which one is cipher data of an unencrypted 7z file that contains an unencrypted 7z file and a text file. The innermost 7z file contains *_prims.h files for soa-encrypter1 and soa-decrypter1. The text file contains encryption parameters for soa-encrypter2/SoA.cipher2.
- ***SoA.cipher3.7z***: Contains 65537 binary files, of which one is SoA.cipher3, the final cipher data of SoA.

#### *parameters* directory:

- ***bravo-params***: Text file containing encryption parameters for bravo-encrypter/bravo.7z.cipher.

#### *source* directory:

- ***alpha-encrypter.7z***: Source code of the encrypter for "Alpha" cipher source code. It is to be used to decrypt alpha.7z.cipher.
- ***bravo-encrypter.7z***: Source code of the encrypter for "Bravo" cipher source code. It is to be used to decrypt bravo.7z.cipher.
- ***filexor.7z***: Source code of filexor. It is to be used to decrypt SoA.cipher3 to SoA.cipher2.
- ***fsrng.7z***: Source code of fsrng, which was used to generate mask/decoy files in prims1_params2.7z and SoA.cipher3.7z. Not needed for decrypting SoA.
- ***soa-decrypter1.7z***: Source code of soa-decrypter1. It is to be used to decrypt SoA.cipher1 to the plaintext of SoA.
- ***soa-encrypter1.7z***: Incomplete source code of soa-encrypter1, which was used to encrypt the plaintext of SoA to SoA.cipher1 in a minimalist dump device. For demonstration purpose only. Not needed for decrypting SoA.
- ***soa-encrypter2.7z***: Source code of soa-encrypter2. It is to be used to decrypt SoA.cipher2 to SoA.cipher1.

### SHA256 checksums

- alpha.7z.cipher: 54b58916ddafde94b4528223f2ed90196fbe3500591da3e6486a2c97060a1c3a
- bravo.7z.cipher: 5557c3584623aab36b1caeaf7b82ea11100044a82e892344732369472b6a2eb8
- prims1_params2.7z: f97248a6a3d705083394af909f820327363fae58edd9b9ccde44c9a98ae78044
- SoA.cipher3.7z: c4a0b4b956dd33ff620e0e5981f33440487ee69c26d7c3d674abd2285a112602
- bravo-params: fe1dd10d3826e8d892fbe0f518c7d5d329e9c4dfae6a96b208dd58289fe7c265
- alpha-encrypter.7z: f5b59e7332102521ca36c857e60dbc568a49680a6a155d1ffff04c6cdf61b814
- bravo-encrypter.7z: b8d8e025845b97c82dd6867fe8f7616bcc0efc75db8538e4e86db51509a90865
- filexor.7z: 9dfd971904ec235f14f18e0983187834ca0e21cfcdac518bc12ead993f102652
- fsrng.7z: d23e90fd1773020138b80dd6d41e123ec4c72feca81a9a14c3a2be309deee91e
- soa-decrypter1.7z: 43435b853f504c65be47f74f58e0fdd8580b99c2ea26f0d1f62bce92712e1c9f
- soa-encrypter1.7z: 8e94b07fd40f2c20b6a030a1672186e72404d972d7d840a7a9dbdef64d51f668
- soa-encrypter2.7z: c78a1dcd3d00ba911a2397d05d7fd80aec6eb2e523382da00d3063f52cc15055

The checksums have been double-checked to be correct.

### How to decrypt

1. Compile alpha-encrypter.
2. Decrypt "Alpha" cipher source code with alpha.7z.cipher and alpha-encrypter.
3. Compile bravo-encrypter with the decrypted Alpha cipher source code.
4. Decrypt "Bravo" cipher source code with bravo.7z.cipher, bravo-encrypter and the provided parameters.
5. Compile soa-encrypter2 with the decrypted Alpha cipher and Bravo cipher source code.
6. Establish soa-decrypter1's primitive configurations (*_prims.h) and soa-encrypter2's parameters. This can be done in two ways:
  - Identify the correct cipher data file in prims1_params2.7z. Decrypt it with undisclosed decrypter(s) to a 7z file that contains them.
  - Brute-force all possibilities.
7. Compile soa-decrypter1 with the decrypted Alpha cipher and Bravo cipher source code, the established primitive configurations, and undisclosed modification(s) on the professional primitives used.
8. Identify the correct SoA.cipher3 file in SoA.cipher3.7z. Rename it to "SoA.cipher3".
9. Rename "65537" file, if existing, to SoA.cipher3's original filename.
10. Decrypt SoA.cipher3 to SoA.cipher2 with filexor and the other files from SoA.cipher3.7z.
11. Decrypt SoA.cipher2 to SoA.cipher1 with soa-encrypter2 and the established parameters.
12. Decrypt SoA.cipher1 to the plaintext of SoA with soa-decrypter1 and undisclosed parameters.

The decryption process has been verified three times with the provided files only, from the beginning to the end, except that the last step was verified with the full soa-encrypter1 in the device. soa-decrypter1 has been verified with test data uncountable times in the development phase and three times in the verification phase to be compatible with the full soa-encrypter1. In other words, with the provided files and correct information, it is guaranteed that SoA can be decrypted.

### How encryption was done

The following steps were performed to generate the files in SoA.cipher3.7z:

- The plaintext of SoA, its encryption passphrase, salt, and other parameters were entered into a device that did not support any ordinary peripherals, including keyboards, mice, and touchscreens, with specifically developed primitive text entering and editing mechanisms.
- The plaintext of SoA was encrypted with the full soa-encrypter1 in the device, resulting in SoA.cipher1, which was transferred to the PC.
- SoA.cipher1 was encrypted with soa-encrypter2, resulting in SoA.cipher2.
- fsrng was run to create 65536 mask files for SoA.cipher2.
- filexor was run on SoA.cipher2 with the mask files, resulting in SoA.cipher3.
- A number between 1 and 65537 inclusive was picked. If the number was not 65537, the mask file of which the name was the number was renamed to "65537". SoA.cipher3 was renamed to the picked number.

### Security measures

The plaintext of SoA, the encryption passphrase, salt, and other parameters for soa-encrypter1 have only ever been entered into the device.

All sensitive information entered on the PC, which was air-gapped the whole time, during encryption and verifications, such as the passphrases, was entered with the mouse-dragging technique described in *How to enter sensitive information on a PC with a keylogger or key-logging keyboard*.

After the verifications, the device was wiped, destroyed, then securely disposed; all relevant files, except the provided ones, which were in TrueCrypt volumes with triple encryption, all TrueCrypt volume files, which were in eCryptfs-encrypted home directory, and all relevant partitions, which were on an HDD (not SSD), were securely wiped and filled with various tools, in various environments, and on all possible levels a large amount of times/passes.

All the remaining information required to decrypt SoA exists in the form of memory only.

### How to interpret SoA

Due to various reasons, including but not limited to the difficulty of text entering and editing, the length of the plaintext of SoA is limited to 1023 characters, which is far from enough to cover all the knowledge available. In order to squeeze in as much information as possible, measures have been taken. Besides all sentences are made as concise as possible, substitutes, abbreviations, and acronyms, including ad hocly defined ones, are widely used; omissions and clauses are used, too.

#### Substitutes, abbreviations, and acronyms

* Predefined:
  * "aging" is substituted with "@".
  * "disease" is substituted with "ds".
  * "death" is substituted with "dx".
  * "lifespan" is substituted with "ls".
  * ", which" is substituted with ",<".
  * "@RC" represents "aging-related changes" or "aging-related conditions".
  * "=>" represents "cause"/"causes"/"causing", "result in"/"results in"/"resulting in" or "lead to"/"leads to"/"leading to", or sometimes "cause"/"causes" as a noun.

* Ad hocly defined single-word abbreviations:
  * '\*' and '#' immediately following a word defines an abbreviation of the word as the first letter of the word followed by the symbol. For example, "work\*" defines an abbreviation as "w\*", which represents "work"; "wood#" defines an abbreviation as "w#", which represents "wood"; "w#w\*" after the definitions means  "woodwork".

* Ad hocly defined acronyms:
  * ']' and '}' immediately following a word defines an acronym in uppercase. ']' defines an acronym of the two words immediately before it. '}' defines an acronym of the three words immediately before it. For example, "work life]" defines an acronym as "WL", which represents "work life", and "work life balance}" defines an acronym as "WLB", which represents "work life balance". Symbols between words are preserved. For example, "work-life-balance}" defines an acronym as "WLB" and it represents "work-life-balance".

The definitions and uses of the substitutes, abbreviations, and acronyms can be combined. For example, if "work life]" and "balance\*" have appeared, "WL b\*}" means "work life balance", and, in the meanwhile, the acronym "WLB" is defined for later uses, e.g., "WLB slows down @ and delays dx" means "work life balance slows down aging and delays death".

Common substitutes, such as "&" for "and", abbreviations, and acronyms, including informal ones, are used when applicable.

Scientific substitutes, abbreviations, and acronyms are used when applicable.

#### Omissions

Periods in substitutes, such as the ones in "e.g.", are omitted.

Some words, such as "the", when not providing essential information, are omitted.

Plural forms are often neglected, especially in substitutes, abbreviations, and acronyms.

#### Clauses

Most @RC are not explained in SoA because they are considered relatively straightforward once SoA is understood. Only a handful of @RC, which are considered not straightforward, are explained in SoA. The explanations are mostly inserted into the sentences in the form of clauses, such as the "=>" ones. The clauses divert the focuses, narrow the views, and cripple the generalization of the original sentences.

In order to correctly and fully understand SoA, create another text from the original text with all clauses addressing individual @RC removed and thoroughly study it before exploring the original text. Only refer to the latter to understand the @RC in the clauses.
