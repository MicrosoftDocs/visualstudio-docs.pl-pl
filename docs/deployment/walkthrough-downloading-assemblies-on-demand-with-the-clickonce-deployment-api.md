---
title: 'Przewodnik: Pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 99d8804b5c6050665508a9a1a6edc8b37fe7ff0c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405860"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Przewodnik: Pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce
Domyślnie wszystkie zestawy zawarte w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zostaną pobrane po pierwszym uruchomieniu aplikacji. Jednak mogą mieć części aplikacji, które są używane w małej grupie użytkowników. W tym przypadku chcesz pobrać zestaw tylko wtedy, gdy tworzysz w jednym z jej typów. Następujące Instruktaż pokazuje, jak oznaczyć określone zestawy w aplikacji jako "opcjonalny", jak je pobrać za pomocą klasy i w <xref:System.Deployment.Application> przestrzenią nazw, gdy wymagane przez środowisko uruchomieniowe języka wspólnego (CLR).

> [!NOTE]
> Aplikacja będzie mieć do uruchamiania w trybie pełnego zaufania, aby użyć tej procedury.

## <a name="prerequisites"></a>Wymagania wstępne
 Potrzebujesz jednego z następujących składników w celu przeprowadzenia tego instruktażu:

- Windows SDK. Zestaw Windows SDK można pobrać z Microsoft Download Center.

- Program Visual Studio.

## <a name="create-the-projects"></a>Tworzenie projektów

#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Aby utworzyć projekt, który używa zestawu na żądanie

1. Utwórz katalog o nazwie ClickOnceOnDemand.

2. Otwórz wiersz polecenia programu Windows SDK lub [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia.

3. Przejdź do katalogu ClickOnceOnDemand.

4. Wygeneruj parę kluczy publiczny/prywatny, korzystając z następującego polecenia:

   ```cmd
   sn -k TestKey.snk
   ```

5. Za pomocą Notatnika lub innego edytora tekstu, zdefiniuj klasę o nazwie `DynamicClass` za pomocą pojedynczej właściwości o nazwie `Message`.

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]

6. Zapisz tekst w pliku o nazwie *ClickOnceLibrary.cs* lub *ClickOnceLibrary.vb*, w zależności od języka, możesz użyć do *ClickOnceOnDemand* katalogu.

7. Skompiluj plik do zestawu.

   ```csharp
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs
   ```

   ```vb
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb
   ```

8. Aby uzyskać token klucza publicznego dla zestawu, należy użyć następującego polecenia:

   ```cmd
   sn -T ClickOnceLibrary.dll
   ```

9. Utwórz nowy plik przy użyciu tekstu w edytorze, a następnie wprowadź poniższy kod. Ten kod tworzy aplikację Windows Forms, która pobiera zestawu ClickOnceLibrary, gdy jest to wymagane.

     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]

10. W kodzie, Znajdź wywołanie <xref:System.Reflection.Assembly.LoadFile%2A>.

11. Ustaw`PublicKeyToken` wartość, która pobranym wcześniej.

12. Zapisz plik jako *Form1.cs* lub *Form1.vb*.

13. Skompiluj go do pliku wykonywalnego przy użyciu następującego polecenia.

    ```csharp
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs
    ```

    ```vb
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb
    ```

## <a name="mark-assemblies-as-optional"></a>Oznacz zestawy jako opcjonalne

#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Aby oznaczyć zestawów jako opcjonalne w aplikacji ClickOnce za pomocą MageUI.exe

1. Za pomocą *MageUI.exe*, utworzyć manifest aplikacji, zgodnie z opisem w [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Manifest aplikacji, użyj następujących ustawień:

    - Nazwy w manifeście aplikacji `ClickOnceOnDemand`.

    - Na **pliki** strony w *ClickOnceLibrary.dll* wierszy, ustawianie **typ pliku** kolumny **Brak**.

    - Na **pliki** stronie *ClickOnceLibrary.dll* wiersz, wpisz `ClickOnceLibrary.dll` w **grupy** kolumny.

2. Za pomocą *MageUI.exe*, utworzyć manifest wdrożenia, zgodnie z opisem w [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Manifest wdrożenia, użyj następujących ustawień:

    - Nazwa pliku manifestu wdrożenia `ClickOnceOnDemand`.

## <a name="testing-the-new-assembly"></a>Testowanie nowego zestawu

#### <a name="to-test-your-on-demand-assembly"></a>Aby przetestować zestaw na żądanie

1. Przekaż swoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia na serwerze sieci Web.

2. Rozpocznij aplikacja wdrożona za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] z przeglądarki internetowej, wprowadzając adres URL do manifestu wdrażania. Jeśli wywołasz swoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji `ClickOnceOnDemand`i przekaż go do katalogu głównego domeny adatum.com, adres URL będzie wyglądać następująco:

   ```
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application
   ```

3. Gdy pojawi się główny formularz, naciśnij klawisz <xref:System.Windows.Forms.Button>. Powinien zostać wyświetlony ciąg w okno komunikatu, która odczytuje "Hello, World!".

## <a name="see-also"></a>Zobacz także
- <xref:System.Deployment.Application.ApplicationDeployment>