---
title: 'Przewodnik: Pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 767c1b93972a5e8fc78b7de46a69d8f464fe85cc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796172"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Przewodnik: Pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie wszystkie zestawy zawarte w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji zostaną pobrane po pierwszym uruchomieniu aplikacji. Jednak mogą mieć części aplikacji, które są używane w małej grupie użytkowników. W tym przypadku chcesz pobrać zestaw tylko wtedy, gdy tworzysz w jednym z jej typów. Następujące Instruktaż pokazuje, jak oznaczyć określone zestawy w aplikacji jako "opcjonalny", jak je pobrać za pomocą klasy i w <xref:System.Deployment.Application> przestrzenią nazw, gdy wymagane przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
> [!NOTE]
>  Aplikacja będzie mieć do uruchamiania w trybie pełnego zaufania, aby użyć tej procedury.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebujesz jednego z następujących składników w celu przeprowadzenia tego instruktażu:  
  
-   Windows SDK. Zestaw Windows SDK można pobrać z Microsoft Download Center.  
  
-   Program Visual Studio.  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Aby utworzyć projekt, który używa zestawu na żądanie  
  
1.  Utwórz katalog o nazwie ClickOnceOnDemand.  
  
2.  Otwórz wiersz polecenia programu Windows SDK lub [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wiersza polecenia.  
  
3.  Przejdź do katalogu ClickOnceOnDemand.  
  
4.  Wygeneruj parę kluczy publiczny/prywatny, korzystając z następującego polecenia:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Za pomocą Notatnika lub innego edytora tekstu, zdefiniuj klasę o nazwie `DynamicClass` za pomocą pojedynczej właściwości o nazwie `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6.  Zapisz tekst w pliku o nazwie `ClickOnceLibrary.cs` lub `ClickOnceLibrary.vb`, w zależności od języka, możesz użyć do katalogu ClickOnceOnDemand.  
  
7.  Skompiluj plik do zestawu.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Aby uzyskać token klucza publicznego dla zestawu, należy użyć następującego polecenia:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Utwórz nowy plik przy użyciu tekstu w edytorze, a następnie wprowadź poniższy kod. Ten kod tworzy aplikację Windows Forms, która pobiera zestawu ClickOnceLibrary, gdy jest to wymagane.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. W kodzie, Znajdź wywołanie <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Ustaw`PublicKeyToken` wartość, która pobranym wcześniej.  
  
12. Zapisz plik jako `Form1.cs` lub `Form1.vb`.  
  
13. Skompiluj go do pliku wykonywalnego przy użyciu następującego polecenia.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Oznaczanie zestawów jako opcjonalne  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Aby oznaczyć zestawów jako opcjonalne w aplikacji ClickOnce za pomocą MageUI.exe  
  
1.  Przy użyciu MageUI.exe, utworzyć manifest aplikacji, zgodnie z opisem w [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Manifest aplikacji, użyj następujących ustawień:  
  
    -   Nazwy w manifeście aplikacji `ClickOnceOnDemand`.  
  
    -   Na **pliki** strony, w wierszu ClickOnceLibrary.dll ustaw **typ pliku** kolumny **Brak**.  
  
    -   Na **pliki** strony w wierszu ClickOnceLibrary.dll typu `ClickOnceLibrary.dll` w **grupy** kolumny.  
  
2.  Za pomocą MageUI.exe, Utwórz manifest wdrożenia, zgodnie z opisem w [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Manifest wdrożenia, użyj następujących ustawień:  
  
    -   Nazwa pliku manifestu wdrożenia `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Testowanie nowego zestawu  
  
#### <a name="to-test-your-on-demand-assembly"></a>Aby przetestować zestaw na żądanie  
  
1.  Przekaż swoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia na serwerze sieci Web.  
  
2.  Rozpocznij aplikacja wdrożona za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] z przeglądarki internetowej, wprowadzając adres URL do manifestu wdrażania. Jeśli wywołasz swoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji `ClickOnceOnDemand`i przekaż go do katalogu głównego domeny adatum.com, adres URL będzie wyglądać następująco:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Gdy pojawi się główny formularz, naciśnij klawisz <xref:System.Windows.Forms.Button>. Powinien zostać wyświetlony ciąg w okno komunikatu, która odczytuje "Hello, World!".  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application.ApplicationDeployment>
