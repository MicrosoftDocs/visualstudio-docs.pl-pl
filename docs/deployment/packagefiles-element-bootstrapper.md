---
title: '&lt;PackageFiles — &gt; element (program inicjujący) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81a12f400ee870798759237e202d2ca358fefa69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "66747511"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles — &gt; element (program inicjujący)
`PackageFiles`Element zawiera `PackageFile` elementy, które definiują pakiety instalacyjne wykonywane w wyniku `Command` elementu.

## <a name="syntax"></a>Składnia

```xml
<PackageFiles
    CopyAllPackageFiles
>
    <PackageFile
        Name
        HomeSite
        CopyOnBuild
        PublicKey
        Hash
    />
</PackageFiles>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `PackageFiles`Element ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`CopyAllPackageFiles`|Opcjonalny. Jeśli jest ustawiona na `false` , instalator pobierze tylko pliki, do których odwołuje się `Command` element. Jeśli jest ustawiona na `true` , zostaną pobrane wszystkie pliki.<br /><br /> Jeśli jest ustawiona na `IfNotHomesite` , Instalator będzie zachowywać się tak samo, jak Jeśli `False` `ComponentsLocation` jest ustawiona na `HomeSite` , a w przeciwnym razie będzie działać tak samo jak w przypadku `True` . To ustawienie może być przydatne, aby zezwalać na pakiety, które same uruchamiają program inicjujący, aby wykonywały własne zachowanie w scenariuszu HomeSite.<br /><br /> Wartość domyślna to `true`.|

## <a name="packagefile"></a>PackageFile
 `PackageFile`Element jest elementem podrzędnym `PackageFiles` elementu. `PackageFiles`Element musi zawierać co najmniej jeden `PackageFile` element.

 `PackageFile` ma następujące atrybuty.

| Atrybut | Opis |
|---------------| - |
| `Name` | Wymagany. Nazwa pliku pakietu. Jest to nazwa, do której `Command` element będzie się odwoływać podczas definiowania warunków, w których pakiet jest instalowany. Ta wartość jest również używana jako klucz w `Strings` tabeli w celu pobrania zlokalizowanej nazwy, która [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] będzie używana przez narzędzia do opisywania pakietu. |
| `HomeSite` | Opcjonalny. Lokalizacja pakietu na serwerze zdalnym, jeśli nie jest zawarta w instalatorze. |
| `CopyOnBuild` | Opcjonalny. Określa, czy program inicjujący powinien skopiować plik pakietu na dysk w czasie kompilacji. Wartość domyślna to true. |
| `PublicKey` | Zaszyfrowany klucz publiczny podpisującego certyfikat pakietu. Wymagane `HomeSite` , jeśli jest używany; w przeciwnym razie opcjonalny. |
| `Hash` | Opcjonalny. Skrót SHA1 pliku pakietu. Służy do weryfikowania integralności pliku w czasie instalacji. Jeśli tego samego skrótu nie można obliczyć z pliku pakietu, pakiet nie zostanie zainstalowany. |

## <a name="example"></a>Przykład
 Poniższy przykład kodu definiuje pakiety dla .NET Framework pakiet redystrybucyjny i jego zależności, takie jak Instalator Windows.

```xml
<PackageFiles>
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetchk.exe"/>
</PackageFiles>
```

## <a name="see-also"></a>Zobacz też
- [\<Product> postaci](../deployment/product-element-bootstrapper.md)
- [\<Package> postaci](../deployment/package-element-bootstrapper.md)
- [Dokumentacja schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)