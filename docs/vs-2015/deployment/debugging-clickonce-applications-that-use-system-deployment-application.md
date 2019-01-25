---
title: Debugowanie aplikacji ClickOnce używających System.Deployment.Application | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0b12faf451d3ed9bb70e2bb1ec6c8503cfb86d5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790605"
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Debugowanie aplikacji ClickOnce używających System.Deployment.Application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia można skonfigurować sposób aktualizowania aplikacji. Jednakże, jeśli chcesz dostosować zaawansowane [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] funkcje wdrażania, konieczne będzie dostępu do modelu obiektu wdrożenia, które są dostarczane przez <xref:System.Deployment.Application>. Możesz użyć <xref:System.Deployment.Application> interfejsów API na potrzeby zaawansowanych zadań, takich jak:  
  
- Tworzenie opcję "Aktualizuj" w aplikacji  
  
- Warunkowe, pobiera na żądanie z różnych składników aplikacji  
  
- Aktualizacje zintegrowana bezpośrednio z aplikacji  
  
- Zagwarantowanie, że aplikacja kliencka jest zawsze aktualny  
  
  Ponieważ <xref:System.Deployment.Application> działają interfejsy API, tylko wtedy, gdy aplikacja jest wdrażana przy użyciu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] technologii, jedynym sposobem debugowania ich jest wdrożenie aplikacji przy użyciu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], Dołącz do niej, a następnie jej debugowania. Może być trudne dołączyć debuger, wczesne, ponieważ ten kod uruchamia często, gdy aplikacja uruchamia się i wykonuje, zanim będzie możliwe dołączenie debugera. To rozwiązanie jest umieścić podziałów (lub zatrzymuje w projektach języka Visual Basic) przed kodu sprawdzania aktualizacji lub kodu na żądanie.  
  
  To zalecana technika debugowania jest następująca:  
  
1. Przed rozpoczęciem upewnij się, że symboli (.pdb) i plików źródłowych są archiwizowane.  
  
2. Wdrażanie aplikacji w wersji 1.  
  
3. Utwórz nowe, puste rozwiązanie. Z **pliku** menu, kliknij przycisk **New**, następnie **projektu**. W **nowy projekt** po otwarciu okna dialogowego **inne typy projektów** węzła, następnie wybierz pozycję **Visual Studio Solutions** folderu. W **szablony** okienku wybierz **puste rozwiązanie**.  
  
4. Dodaj lokalizację źródłową zarchiwizowane do właściwości dla tego nowego rozwiązania. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, a następnie kliknij przycisk **właściwości**. W **stron właściwości** okno dialogowe, wybierz opcję **Debuguj pliki źródłowe**, następnie dodaj katalog kodu źródłowego zarchiwizowane. W przeciwnym razie debugera zawiera pliki źródłowe nieaktualne, ponieważ ścieżki plików źródłowych są rejestrowane w pliku .pdb. Jeśli debuger używa plików źródłowych nieaktualne, zobaczysz komunikat informujący, że źródło nie jest zgodny.  
  
5. Upewnij się, że debuger można znaleźć w plikach .pdb. Jeśli wdrożono je z aplikacją, debuger wykryje je automatycznie. Zawsze szuka obok zestawu w danym najpierw. W przeciwnym razie konieczne będzie dodanie ścieżki archiwum do **symboli (.pdb) lokalizacji** (dostęp do tej opcji z **narzędzia** menu, kliknij przycisk **opcje**, otwórz  **Debugowanie** węzeł, a następnie kliknij przycisk **symbole**).  
  
6. Debugowanie, co się stanie, między `CheckForUpdate` i `Download` / `Update` wywołania metody.  
  
    Na przykład kod aktualizacji może wyglądać następująco:  
  
   ```  
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. Wdrażanie w wersji 2.  
  
8. Podjęto próbę dołączenia debugera do aplikacji w wersji 1, jako pliki do pobrania aktualizacji w wersji 2. Możesz też użyć `System.Diagnostics.Debugger.Break` metody lub po prostu `Stop` w języku Visual Basic. Oczywiście nie opuszczaj te wywołania metody w kodzie produkcyjnym.  
  
    Załóżmy na przykład, tworzenia aplikacji Windows Forms, a masz program obsługi zdarzeń dla tej metody wraz z logiką aktualizacji w nim. Do debugowania tego, po prostu dołączyć, zanim przycisk jest wciśnięty, a następnie ustaw punkt przerwania (Upewnij się, otwórz odpowiedni plik zarchiwizowanego, a następnie ustaw punkt przerwania ma).  
  
   Użyj <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> właściwości do wywołania <xref:System.Deployment.Application> interfejsów API, tylko wtedy, gdy aplikacja jest wdrażana; interfejsów API, nie powinna być wywoływana podczas debugowania w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application>
