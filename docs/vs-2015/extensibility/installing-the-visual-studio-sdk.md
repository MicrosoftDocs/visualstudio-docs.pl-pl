---
title: Instalowanie programu Visual Studio SDK | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1da992ebdb5c3d4e0381cdc388dcf6ad5d2af66c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091151"
---
# <a name="installing-the-visual-studio-sdk"></a>Instalowanie programu Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalowanie programu Visual Studio SDK w ramach instalacji programu Visual Studio  
 Jeśli chcesz uwzględnić VSSDK w instalacji programu Visual Studio, należy wykonać instalację niestandardową.  
  
> [!NOTE]
>  W pliku wykonywalnego instalacji programu Visual Studio SDK jest nazywany **Visual Studio Extensibility Tools**.  
  
1. Uruchom instalację programu Visual Studio 2015. Można zainstalować w każdej wersji programu Visual Studio, z wyjątkiem Express.  
  
2. Na pierwszym ekranie Wybierz **niestandardowe**, a nie **domyślne**. Kliknij przycisk **Dalej**.  
  
3. Powinien zostać wyświetlony w widoku drzewa funkcji niestandardowych. Otwórz **popularnych narzędzi**. Powinien zostać wyświetlony **Visual Studio Extensibility Tools** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. Sprawdź **Visual Studio Extensibility Tools** , następnie kliknij przycisk **dalej** i kontynuować instalację.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalowanie zestawu SDK programu Visual Studio po zainstalowaniu programu Visual Studio  
 Jeśli zdecydujesz się zainstalować zestawu SDK programu Visual Studio po zakończeniu instalacji programu Visual Studio, powinny wykonaj następującą procedurę:  
  
1. Przejdź do **Panel sterowania / Programy / programy i funkcje**i poszukaj **programu Visual Studio 2015**. Można zainstalować programu Visual Studio SDK dla dowolnej wersji programu Visual Studio 2015, z wyjątkiem Express.  
  
2. Kliknij prawym przyciskiem myszy **programu Visual Studio 2015**, a następnie kliknij przycisk **zmiany**. Powinna zostać wyświetlona strona instalacji.  
  
3. Wykonaj tę samą procedurę jak **Instalowanie zestawu SDK programu Visual Studio jako część instalacji programu Visual Studio** powyżej.  
  
4. Kliknij przycisk **Visual Studio Extensibility Tools** link, aby zainstalować program Visual Studio SDK.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalowanie zestawu SDK programu Visual Studio za pomocą rozwiązania  
 Po otwarciu rozwiązania z projektem rozszerzalności bez instalowania najpierw oprogramowania VSSDK zostanie wyświetlony monit, wyróżnione pasek powyżej Eksploratora rozwiązań. Powinien on wyglądać podobnie do poniższych:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalowanie programu Visual Studio SDK z poziomu wiersza polecenia  
 VSSDK można zainstalować z poziomu wiersza polecenia, za pomocą **/installselectableitems są** przełączyć z Instalatorem programu Visual Studio. Aby uzyskać szczegółowe informacje o korzystaniu z parametrów wiersza polecenia z Instalatorem, zobacz [instalowania programu Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Poniżej przedstawiono sposób instalowania VSSDK dyskretnie za pomocą Instalatora programu Visual Studio 2015 Community:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Należy pamiętać, że należy użyć Instalatora programu Visual Studio, która jest zgodna z zainstalowaną wersją programu Visual Studio. Na przykład w przypadku programu Visual Studio Enterprise zainstalowana na danym komputerze należy uruchomić Instalatora programu Visual Studio Enterprise (vs_enterprise.exe).
