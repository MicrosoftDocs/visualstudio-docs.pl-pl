---
title: Debuguj aplikacje ClickOnce używające System. Deployment. Application
description: Dowiedz się, jak używać i dostosowywać zaawansowane funkcje wdrażania ClickOnce, uzyskując dostęp do modelu obiektów wdrożenia dostarczonego przez system. Deployment. Application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6a014afff6c26b8cfe8f4f7fae508f78ef5905f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912250"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Debuguj aplikacje ClickOnce używające System. Deployment. Application
W [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] programie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie umożliwia skonfigurowanie sposobu aktualizowania aplikacji. Jeśli jednak zachodzi potrzeba użycia i dostosowania zaawansowanych [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funkcji wdrażania, należy uzyskać dostęp do modelu obiektów wdrożenia dostarczonego przez program <xref:System.Deployment.Application> . Możesz użyć <xref:System.Deployment.Application> interfejsów API do zadań zaawansowanych, takich jak:

- Tworzenie opcji "Aktualizuj teraz" w aplikacji

- Na żądanie pobierane są różne składniki aplikacji

- Aktualizacje zintegrowane bezpośrednio z aplikacją

- Zagwarantowanie, że aplikacja kliencka jest zawsze aktualna

  Ponieważ <xref:System.Deployment.Application> interfejsy API działają tylko wtedy, gdy aplikacja jest wdrażana za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologii, jedynym sposobem debugowania jest wdrożenie aplikacji za pomocą programu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , dołączenie do niej, a następnie debugowanie. Może być trudne dołączenie debugera wystarczająco wcześnie, ponieważ ten kod często działa podczas uruchamiania i wykonywania aplikacji przed dołączeniem debugera. Rozwiązanie polega na umieszczeniu przerw (lub zatrzymywania dla Visual Basic projektów) przed aktualizacją kodu sprawdzania lub kodem na żądanie.

  Zalecana technika debugowania jest następująca:

1. Przed rozpoczęciem upewnij się, że jest archiwizowany symbol (. pdb) i pliki źródłowe.

2. Wdróż wersję 1 aplikacji.

3. Utwórz nowe puste rozwiązanie. W menu **plik** kliknij pozycję **Nowy**, a następnie polecenie **projekt**. W oknie dialogowym **Nowy projekt** Otwórz węzeł **Inne typy projektów** , a następnie wybierz folder **rozwiązania programu Visual Studio** . W okienku **Szablony** wybierz pozycję **puste rozwiązanie**.

4. Dodaj zarchiwizowaną lokalizację źródłową do właściwości tego nowego rozwiązania. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł rozwiązanie, a następnie kliknij polecenie **Właściwości**. W oknie dialogowym **strony właściwości** wybierz pozycję **Debuguj pliki źródłowe**, a następnie Dodaj katalog archiwalnego kodu źródłowego. W przeciwnym razie debuger odnajdzie nieaktualne pliki źródłowe, ponieważ ścieżki plików źródłowych są zapisywane w pliku. pdb. Jeśli debuger używa nieaktualnych plików źródłowych, zobaczysz komunikat informujący, że źródło nie jest zgodne.

5. Upewnij się, że debuger może znaleźć pliki *. pdb* . Jeśli zostały wdrożone w aplikacji, debuger odnajdzie je automatycznie. Jest on zawsze wyglądał obok zestawu w polu pytanie. W przeciwnym razie należy dodać ścieżkę archiwalną do **lokalizacji pliku symboli (. pdb)** (Aby uzyskać dostęp do tej opcji, w menu **Narzędzia** kliknij pozycję **Opcje**, a następnie otwórz węzeł **debugowanie** i kliknij pozycję **symbole**).

6. Debuguj, co się dzieje `CheckForUpdate` między `Download` / `Update` wywołaniami metody a.

    Na przykład kod aktualizacji może być następujący:

   ```vb
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
           If My.Application.Deployment.IsNetworkDeployed Then

               If (My.Application.Deployment.CheckForUpdate()) Then

                   My.Application.Deployment.Update()
                   Application.Restart()

               End If

           End If
       End Sub
   ```

7. Wdróż wersję 2.

8. Podjęto próbę dołączenia debugera do aplikacji w wersji 1 w miarę pobierania aktualizacji dla wersji 2. Alternatywnie możesz użyć `System.Diagnostics.Debugger.Break` metody lub po prostu `Stop` w Visual Basic. Oczywiście nie należy pozostawiać tych wywołań metod w kodzie produkcyjnym.

    Załóżmy na przykład, że tworzysz aplikację Windows Forms i masz procedurę obsługi zdarzeń dla tej metody za pomocą logiki aktualizacji. Aby debugować ten element, po prostu Dołącz przed naciśnięciem przycisku, a następnie ustaw punkt przerwania (Upewnij się, że otwarto odpowiedni zarchiwizowany plik i ustawisz punkt przerwania).

   Użyj <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> właściwości, aby wywołać <xref:System.Deployment.Application> interfejsy API tylko wtedy, gdy aplikacja jest wdrożona; nie należy wywoływać interfejsów API podczas debugowania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Zobacz też
- <xref:System.Deployment.Application>