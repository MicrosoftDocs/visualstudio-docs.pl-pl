---
title: Instalowanie zestawu Visual Studio SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858700"
---
# <a name="installing-the-visual-studio-sdk"></a>Instalowanie zestawu Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalowanie zestawu Visual Studio SDK w ramach instalacji programu Visual Studio  
 Jeśli chcesz uwzględnić VSSDK w instalacji programu Visual Studio, musisz wykonać instalację niestandardową.  
  
> [!NOTE]
> W pliku wykonywalnym Instalatora Visual Studio SDK jest wywoływana **Visual Studio Extensibility Tools**.  
  
1. Uruchom instalację programu Visual Studio 2015. Możesz zainstalować dowolną wersję programu Visual Studio, z wyjątkiem Express.  
  
2. Na pierwszym ekranie wybierz opcję **niestandardowa**, a nie **Domyślna**. Kliknij przycisk **Dalej**.  
  
3. Powinien zostać wyświetlony widok drzewa funkcji niestandardowych. Otwórz okno **popularne narzędzia**. Powinna zostać wyświetlona **Visual Studio Extensibility Tools** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. Zaznacz **Visual Studio Extensibility Tools** , a następnie kliknij przycisk **dalej** i Kontynuuj instalację.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalowanie zestawu Visual Studio SDK po zainstalowaniu programu Visual Studio  
 Jeśli zdecydujesz się zainstalować zestaw SDK programu Visual Studio po zakończeniu instalacji programu Visual Studio, postępuj zgodnie z następującą procedurą:  
  
1. Przejdź do **Panelu sterowania/programy/programy i funkcje**, a następnie wyszukaj **program Visual Studio 2015**. Zestaw Visual Studio SDK można zainstalować dla dowolnej wersji programu Visual Studio 2015 z wyjątkiem języka Express.  
  
2. Kliknij prawym przyciskiem myszy **program Visual Studio 2015**, a następnie kliknij przycisk **Zmień**. Powinna zostać wyświetlona strona instalacji.  
  
3. Postępuj zgodnie z tą samą procedurą jak w **przypadku instalowania programu Visual Studio SDK w ramach instalacji programu Visual Studio** .  
  
4. Kliknij link **Visual Studio Extensibility Tools** , aby zainstalować zestaw Visual Studio SDK.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalowanie zestawu Visual Studio SDK z rozwiązania  
 Jeśli otworzysz rozwiązanie przy użyciu projektu rozszerzalności bez wcześniejszego zainstalowania VSSDK, zostanie wyświetlony monit o wyróżniony pasek informacji powyżej Eksplorator rozwiązań. Powinien wyglądać podobnie do poniższego:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalowanie zestawu Visual Studio SDK z wiersza polecenia  
 Możesz zainstalować VSSDK z wiersza polecenia, używając przełącznika **/InstallSelectableItems** z instalatorem programu Visual Studio. Aby uzyskać szczegółowe informacje o używaniu parametrów wiersza polecenia w instalatorze, zobacz [Instalowanie programu Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Poniżej przedstawiono sposób instalacji VSSDK w trybie cichym przy użyciu Instalatora społeczności programu Visual Studio 2015:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Należy pamiętać, że należy użyć Instalatora programu Visual Studio, który jest zgodny z zainstalowaną wersją programu Visual Studio. Na przykład jeśli na komputerze zainstalowano Visual Studio Enterprise, należy uruchomić Instalatora Visual Studio Enterprise (vs_enterprise.exe).
