---
title: 'Przewodnik: pobieranie zestawów na żądanie przy użyciu interfejsu API wdrażania ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: af03329a05501427f6d04d6cddbd637c3311b339
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804957"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Wskazówki: pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie wszystkie zestawy zawarte w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji są pobierane podczas pierwszego uruchomienia aplikacji. Mogą jednak istnieć części aplikacji, które są używane przez niewielki zestaw użytkowników. W takim przypadku należy pobrać zestaw tylko podczas tworzenia jednego z jego typów. W poniższym instruktażu pokazano, jak oznaczyć pewne zestawy w aplikacji jako "opcjonalne" oraz jak pobierać je przy użyciu klas w <xref:System.Deployment.Application> przestrzeni nazw, gdy program środowiska uruchomieniowego języka wspólnego (CLR) ich żąda.  
  
> [!NOTE]
> Aby można było użyć tej procedury, aplikacja będzie musiała działać w trybie pełnego zaufania.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, musisz mieć jeden z następujących składników:  
  
- Windows SDK. Windows SDK można pobrać z centrum pobierania Microsoft.  
  
- Programu Visual Studio.  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Aby utworzyć projekt, który używa zestawu na żądanie  
  
1. Utwórz katalog o nazwie ClickOnceOnDemand.  
  
2. Otwórz wiersz polecenia Windows SDK lub [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wiersz polecenia.  
  
3. Przejdź do katalogu ClickOnceOnDemand.  
  
4. Wygeneruj parę kluczy publiczny/prywatny przy użyciu następującego polecenia:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5. Za pomocą Notatnika lub innego edytora tekstów, zdefiniuj klasę o nazwie `DynamicClass` z pojedynczą właściwością o nazwie `Message` .  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6. Zapisz tekst jako plik o nazwie `ClickOnceLibrary.cs` lub `ClickOnceLibrary.vb` , w zależności od używanego języka, do katalogu ClickOnceOnDemand.  
  
7. Skompiluj plik do zestawu.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8. Aby uzyskać token klucza publicznego dla zestawu, użyj następującego polecenia:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Utwórz nowy plik za pomocą edytora tekstów i wprowadź następujący kod. Ten kod tworzy aplikację Windows Forms, która pobiera zestaw ClickOnceLibrary, gdy jest to wymagane.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. W kodzie Znajdź wywołanie <xref:System.Reflection.Assembly.LoadFile%2A> .  
  
11. Ustaw `PublicKeyToken` wartość, która została pobrana wcześniej.  
  
12. Zapisz plik jako `Form1.cs` lub `Form1.vb` .  
  
13. Skompiluj ją w pliku wykonywalnym przy użyciu następującego polecenia.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Oznaczanie zestawów jako opcjonalne  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Aby oznaczyć zestawy jako opcjonalne w aplikacji ClickOnce przy użyciu MageUI.exe  
  
1. Korzystając z MageUI.exe, Utwórz manifest aplikacji zgodnie z opisem w [przewodniku: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Użyj następujących ustawień manifestu aplikacji:  
  
    - Nazwij manifest aplikacji `ClickOnceOnDemand` .  
  
    - Na stronie **pliki** w wierszu ClickOnceLibrary.dll ustaw wartość kolumny **Typ pliku** na **Brak**.  
  
    - Na stronie **pliki** w wierszu ClickOnceLibrary.dll wpisz `ClickOnceLibrary.dll` w kolumnie **Grupa** .  
  
2. Korzystając z MageUI.exe, Utwórz manifest wdrożenia zgodnie z opisem w [przewodniku: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Użyj następujących ustawień manifestu wdrożenia:  
  
    - Nazwij manifest wdrożenia `ClickOnceOnDemand` .  
  
## <a name="testing-the-new-assembly"></a>Testowanie nowego zestawu  
  
#### <a name="to-test-your-on-demand-assembly"></a>Aby przetestować zestaw na żądanie  
  
1. Przekaż [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenie na serwer sieci Web.  
  
2. Rozpocznij wdrażanie aplikacji przy użyciu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przeglądarki sieci Web, wprowadzając adres URL do manifestu wdrożenia. Jeśli wywołasz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację `ClickOnceOnDemand` i przekażesz ją do katalogu głównego adatum.com, adres URL będzie wyglądać następująco:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3. Gdy zostanie wyświetlony główny formularz, naciśnij klawisz <xref:System.Windows.Forms.Button> . W oknie komunikatu powinien zostać wyświetlony ciąg, który odczytuje wartość "Hello, World!".  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application.ApplicationDeployment>
