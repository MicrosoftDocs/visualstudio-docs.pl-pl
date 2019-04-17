---
title: 'Instrukcje: Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio 2015 | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656729"
---
# <a name="how-to-automatically-apply-product-keys-when-deploying-visual-studio"></a>Instrukcje: Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](/visualstudio/install/automatically-apply-product-keys-when-deploying-visual-studio).

Można zastosować klucz produktu programowego jako część skryptu, który umożliwia automatyzowanie wdrażania programu Visual Studio 2015. Klucze produktów można ustawić na urządzeniu programowo podczas instalacji programu Visual Studio lub po ukończeniu instalacji.

## <a name="apply-the-license-during-installation"></a>Zastosować licencję podczas instalacji
 Aby zastosować klucz produktu podczas procesu instalacji programu Visual Studio, należy użyć parametru/ProductKey. Ten parametr instalacji może służyć za pomocą/silent parametru, aby zainstalować program Visual Studio w stanie już licencjonowane dla użytkownika końcowego. Aby użyć parametru/ProductKey, otwórz wiersz polecenia. Uruchomienie programu instalacyjnego (na przykład vs_enterprise.exe lub vs_professional.exe) i ustaw dla parametru/ProductKey za pomocą klucza produktu (25 znaków), który zawiera nie kresek:

 To przykładowe polecenie dotyczące instalowania programu Visual Studio Enterprise 2015 z kluczem produktu AAAAABBBBBCCCCCDDDDDEEEEEEE:

 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`

## <a name="apply-the-license-after-installation"></a>Po zainstalowaniu Zastosuj licencji
 Zainstalowana wersja programu Visual Studio za pomocą klucza produktu można aktywować za pomocą narzędzia storePID.exe na komputerach docelowych w trybie dyskretnym. StorePID.exe to program narzędzie instalowanej razem z Visual Studio na  **\<dysku >:\\\Program pliki (x86) \Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe**.

 Uruchom storePID.exe z podwyższonym poziomem uprawnień, przy użyciu agenta programu System Center lub wiersz polecenia, a następnie za pomocą klucza produktu (z kreskami) i kod produktu firmy Microsoft (MPC). Pamiętaj uwzględnić kresek klucz produktu!

 `StorePID.exe [product key including the dashes] [MPC]`

 Oto przykładowy wiersz polecenia dotyczące instalowania programu Visual Studio 2015 Enterprise, która ma MPC 07060, za pomocą klucza produktu "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE":

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

Aby uzyskać więcej informacji na temat pobierania klucza produktu, zobacz [jak: Znajdź klucz produktu programu Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md).

StorePID.exe pomyślnie zastosować klucz produktu, zwróci 0. W przypadku wykrycia błędów, zwróci liczbę z zakresu od 1 do 6.

## <a name="see-also"></a>Zobacz także

- [Instalowanie programu Visual Studio](../install/install-visual-studio-2015.md)