---
title: 'Instrukcje: automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio 2015 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 11
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ec050cf8f365bfae2290593a0c7f215dcb2f39cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185998"
---
# <a name="how-to-automatically-apply-product-keys-when-deploying-visual-studio"></a>Porady: automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](/visualstudio/install/automatically-apply-product-keys-when-deploying-visual-studio).

Możesz programowo zastosować swój klucz produktu w ramach skryptu służącego do automatyzowania wdrożenia programu Visual Studio 2015. Klucze produktów można ustawiać na urządzeniu programowo podczas instalacji programu Visual Studio lub po zakończeniu instalacji.

## <a name="apply-the-license-during-installation"></a>Zastosuj licencję podczas instalacji
 Użyj parametru/ProductKey, aby zastosować klucz produktu podczas procesu instalacji programu Visual Studio. Tego parametru instalacji można użyć z parametrem/Silent, aby zainstalować program Visual Studio w stanie już licencjonowanym dla użytkownika końcowego. Aby użyć parametru/ProductKey, Otwórz wiersz polecenia. Uruchom program instalacyjny (na przykład vs_enterprise.exe lub vs_professional.exe) i ustaw parametr/ProductKey za pomocą klucza produktu (25 znaków) bez kresek:

 Jest to przykładowe polecenie służące do instalowania programu Visual Studio 2015 Enterprise z użyciem klucza produktu AAAAABBBBBCCCCCDDDDDEEEEEEE:

 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`

## <a name="apply-the-license-after-installation"></a>Zastosuj licencję po instalacji
 Zainstalowaną wersję programu Visual Studio można aktywować za pomocą klucza produktu przy użyciu narzędzia storePID.exe na komputerach docelowych w trybie dyskretnym. StorePID.exe to program narzędziowy instalowany razem z programem Visual Studio w lokalizacji ** \<drive> : \\ \Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe**.

 Uruchom storePID.exe z podniesionymi uprawnieniami, korzystając z programu System Center Agent lub wiersza polecenia z podwyższonym poziomem uprawnień, a następnie klucza produktu (w tym kresek) i kodu produktu firmy Microsoft (MPC). Pamiętaj o uwzględnieniu kresek w kluczu produktu!

 `StorePID.exe [product key including the dashes] [MPC]`

 Jest to przykładowy wiersz polecenia służący do instalowania programu Visual Studio 2015 Enterprise, który ma MPC 07060 z kluczem produktu "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE":

 `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 07060`

 Poniższa tabela zawiera listę kodów MPC dla każdej wersji programu Visual Studio:

|Wersja programu Visual Studio|MPC|
|---------------------------|---------|
|Visual Studio Enterprise 2015|07060|
|Visual Studio Professional 2015|07062|
|Visual Studio Test Professional 2015|07066|
|Visual Studio Ultimate 2013|06181|
|Visual Studio Premium 2013|06191|
|Visual Studio Professional 2013|06177|
|Visual Studio Test Professional 2013|06194|

Aby uzyskać więcej informacji na temat uzyskiwania klucza produktu, zobacz [How to: Lokalizowanie klucza produktu Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md).

Jeśli StorePID.exe pomyślnie zastosować klucz produktu, zwróci 0. Jeśli wystąpią błędy, zwróci liczbę z zakresu od 1 do 6.

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio](../install/install-visual-studio-2015.md)