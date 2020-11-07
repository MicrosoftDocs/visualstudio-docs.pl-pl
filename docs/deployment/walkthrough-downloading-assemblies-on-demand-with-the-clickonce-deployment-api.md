---
title: Pobierz zestawy na żądanie (interfejs API ClickOnce)
description: Dowiedz się, jak oznaczyć pewne zestawy w aplikacji ClickOnce jako opcjonalne i pobrać je, gdy wymagają ich środowisko uruchomieniowe języka wspólnego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb74d7fd5ad388b9b3dc217bae8782b24517c13b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349267"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Przewodnik: pobieranie zestawów na żądanie przy użyciu interfejsu API wdrażania ClickOnce
Domyślnie wszystkie zestawy zawarte w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji są pobierane podczas pierwszego uruchomienia aplikacji. Mogą jednak istnieć części aplikacji, które są używane przez niewielki zestaw użytkowników. W takim przypadku należy pobrać zestaw tylko podczas tworzenia jednego z jego typów. W poniższym instruktażu pokazano, jak oznaczyć pewne zestawy w aplikacji jako "opcjonalne" oraz jak pobierać je przy użyciu klas w <xref:System.Deployment.Application> przestrzeni nazw, gdy program środowiska uruchomieniowego języka wspólnego (CLR) ich żąda.

> [!NOTE]
> Aby można było użyć tej procedury, aplikacja będzie musiała działać w trybie pełnego zaufania.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, musisz mieć jeden z następujących składników:

- Windows SDK. Windows SDK można pobrać z centrum pobierania Microsoft.

- Programu Visual Studio.

## <a name="create-the-projects"></a>Tworzenie projektów

#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Aby utworzyć projekt, który używa zestawu na żądanie

1. Utwórz katalog o nazwie ClickOnceOnDemand.

2. Otwórz wiersz polecenia Windows SDK lub [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersz polecenia.

3. Przejdź do katalogu ClickOnceOnDemand.

4. Wygeneruj parę kluczy publiczny/prywatny przy użyciu następującego polecenia:

   ```cmd
   sn -k TestKey.snk
   ```

5. Za pomocą Notatnika lub innego edytora tekstów, zdefiniuj klasę o nazwie `DynamicClass` z pojedynczą właściwością o nazwie `Message` .

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]

6. Zapisz tekst jako plik o nazwie *ClickOnceLibrary.cs* lub *ClickOnceLibrary. vb* , w zależności od używanego języka, do katalogu *ClickOnceOnDemand* .

7. Skompiluj plik do zestawu.

   ```csharp
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs
   ```

   ```vb
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb
   ```

8. Aby uzyskać token klucza publicznego dla zestawu, użyj następującego polecenia:

   ```cmd
   sn -T ClickOnceLibrary.dll
   ```

9. Utwórz nowy plik za pomocą edytora tekstów i wprowadź następujący kod. Ten kod tworzy aplikację Windows Forms, która pobiera zestaw ClickOnceLibrary, gdy jest to wymagane.

     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]

10. W kodzie Znajdź wywołanie <xref:System.Reflection.Assembly.LoadFile%2A> .

11. Ustaw `PublicKeyToken` wartość, która została pobrana wcześniej.

12. Zapisz plik jako *Form1.cs* lub *Form1. vb*.

13. Skompiluj ją w pliku wykonywalnym przy użyciu następującego polecenia.

    ```csharp
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs
    ```

    ```vb
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb
    ```

## <a name="mark-assemblies-as-optional"></a>Oznacz zestawy jako opcjonalne

#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Aby oznaczyć zestawy jako opcjonalne w aplikacji ClickOnce przy użyciu MageUI.exe

1. Korzystając z *MageUI.exe* , Utwórz manifest aplikacji zgodnie z opisem w [przewodniku: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Użyj następujących ustawień manifestu aplikacji:

    - Nazwij manifest aplikacji `ClickOnceOnDemand` .

    - Na stronie **pliki** w wierszu *ClickOnceLibrary.dll* ustaw wartość kolumny **Typ pliku** na **Brak**.

    - Na stronie **pliki** w wierszu *ClickOnceLibrary.dll* wpisz `ClickOnceLibrary.dll` w kolumnie **Grupa** .

2. Korzystając z *MageUI.exe* , Utwórz manifest wdrożenia zgodnie z opisem w [przewodniku: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Użyj następujących ustawień manifestu wdrożenia:

    - Nazwij manifest wdrożenia `ClickOnceOnDemand` .

## <a name="testing-the-new-assembly"></a>Testowanie nowego zestawu

#### <a name="to-test-your-on-demand-assembly"></a>Aby przetestować zestaw na żądanie

1. Przekaż [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie na serwer sieci Web.

2. Rozpocznij wdrażanie aplikacji przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przeglądarki sieci Web, wprowadzając adres URL do manifestu wdrożenia. Jeśli wywołasz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację `ClickOnceOnDemand` i przekażesz ją do katalogu głównego adatum.com, adres URL będzie wyglądać następująco:

   ```
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application
   ```

3. Gdy zostanie wyświetlony główny formularz, naciśnij klawisz <xref:System.Windows.Forms.Button> . W oknie komunikatu powinien zostać wyświetlony ciąg, który odczytuje wartość "Hello, World!".

## <a name="see-also"></a>Zobacz też
- <xref:System.Deployment.Application.ApplicationDeployment>