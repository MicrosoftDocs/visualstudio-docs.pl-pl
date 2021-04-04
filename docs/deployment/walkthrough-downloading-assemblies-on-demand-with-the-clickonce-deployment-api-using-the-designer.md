---
title: Pobierz zestawy na żądanie przy użyciu narzędzia Projektant (interfejs API ClickOnce)
description: Dowiedz się, jak oznaczyć pewne zestawy w aplikacji ClickOnce jako opcjonalne przy użyciu narzędzia Projektant i pobrać je, gdy środowisko uruchomieniowe języka wspólnego ich potrzebuje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7bb30b26e859708d295a31bd45b310897e4bcaac
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216998"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Przewodnik: pobieranie zestawów na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu narzędzia Projektant
Domyślnie wszystkie zestawy zawarte w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji są pobierane podczas pierwszego uruchomienia aplikacji. Mogą jednak istnieć części aplikacji, które są używane przez niewielki zestaw użytkowników. W takim przypadku należy pobrać zestaw tylko podczas tworzenia jednego z jego typów. W poniższym instruktażu pokazano, jak oznaczyć pewne zestawy w aplikacji jako "opcjonalne" oraz jak pobrać je przy użyciu klas w <xref:System.Deployment.Application> przestrzeni nazw, gdy środowisko uruchomieniowe języka wspólnego je zażąda.

> [!NOTE]
> Aby można było użyć tej procedury, aplikacja będzie musiała działać w trybie pełnego zaufania.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, kliknij przycisk **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

## <a name="create-the-projects"></a>Tworzenie projektów

### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Aby utworzyć projekt, który używa zestawu na żądanie z programem Visual Studio

1. Utwórz nowy projekt Windows Forms w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . W menu **plik** wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**. W oknie dialogowym wybierz projekt **Biblioteka klas** i nadaj mu nazwę `ClickOnceLibrary` .

   > [!NOTE]
   > W Visual Basic zaleca się zmodyfikowanie właściwości projektu, aby zmienić główną przestrzeń nazw dla tego projektu na `Microsoft.Samples.ClickOnceOnDemand` lub na wybraną przestrzeń nazw. Dla uproszczenia dwa projekty w tym instruktażu znajdują się w tej samej przestrzeni nazw.

2. Zdefiniuj klasę o nazwie `DynamicClass` z pojedynczą właściwością o nazwie `Message` .

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs" id="Snippet1":::

3. Wybierz projekt Windows Forms w **Eksplorator rozwiązań**. Dodaj odwołanie do <xref:System.Deployment.Application> zestawu i odwołania projektu do `ClickOnceLibrary` projektu.

   > [!NOTE]
   > W Visual Basic zaleca się zmodyfikowanie właściwości projektu, aby zmienić główną przestrzeń nazw dla tego projektu na `Microsoft.Samples.ClickOnceOnDemand` lub na wybraną przestrzeń nazw. Dla uproszczenia dwa projekty w tym instruktażu znajdują się w tej samej przestrzeni nazw.

4. Kliknij prawym przyciskiem myszy formularz, kliknij polecenie **Wyświetl kod** z menu i Dodaj następujące odwołania do formularza.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet1":::

5. Dodaj następujący kod, aby pobrać ten zestaw na żądanie. Ten kod przedstawia sposób mapowania zestawu zestawów na nazwę grupy przy użyciu klasy generycznej <xref:System.Collections.DictionaryBase.Dictionary%2A> . Ponieważ pobieramy tylko jeden zestaw z tego przewodnika, w naszej grupie istnieje tylko jeden zestaw. W rzeczywistej aplikacji prawdopodobnie chcesz pobrać wszystkie zestawy powiązane z pojedynczą funkcją w aplikacji w tym samym czasie. Tabela mapowanie pozwala łatwo to zrobić, kojarząc wszystkie biblioteki DLL należące do funkcji z nazwą grupy pobierania.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet2":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet2":::

6. W menu **Widok** kliknij pozycję **Przybornik**. Przeciągnij <xref:System.Windows.Forms.Button> z **przybornika** do formularza. Kliknij dwukrotnie przycisk i Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet3":::

## <a name="mark-assemblies-as-optional"></a>Oznacz zestawy jako opcjonalne

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Aby oznaczyć zestawy jako opcjonalne w aplikacji ClickOnce przy użyciu programu Visual Studio

1. Kliknij prawym przyciskiem myszy projekt Windows Forms w **Eksplorator rozwiązań** a następnie kliknij pozycję **Właściwości**. Wybierz kartę **Publikowanie** .

2. Kliknij przycisk **pliki aplikacji** .

3. Znajdź listę *ClickOnceLibrary.dll*. Ustaw pole listy rozwijanej **stan publikowania** , aby **uwzględnić**.

4. Rozwiń pole listy rozwijanej **Grupa** i wybierz pozycję **Nowy**. Wprowadź nazwę `ClickOnceLibrary` jako nową nazwę grupy.

5. Kontynuuj publikowanie aplikacji zgodnie z opisem w artykule [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Aby oznaczyć zestawy jako opcjonalne w aplikacji ClickOnce przy użyciu Narzędzie tworzenia i edycji manifestów — graficznego klienta (MageUI.exe)

1. Utwórz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty zgodnie z opisem w [przewodniku: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Przed zamknięciem MageUI.exe wybierz kartę, która zawiera manifest aplikacji wdrożenia, a na tej karcie Wybierz kartę **pliki** .

3. Znajdź ClickOnceLibrary.dll na liście plików aplikacji i ustaw dla jego kolumny **Typ pliku** **wartość None**. Dla kolumny **Grupa** wpisz `ClickOnceLibrary.dll` .

## <a name="test-the-new-assembly"></a>Testowanie nowego zestawu

Aby przetestować zestaw na żądanie:

1. Rozpocznij wdrażanie aplikacji za pomocą programu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

2. Gdy zostanie wyświetlony główny formularz, naciśnij klawisz <xref:System.Windows.Forms.Button> . Powinien zostać wyświetlony ciąg w oknie komunikatu z komunikatem "Hello, World!"

## <a name="see-also"></a>Zobacz też

- <xref:System.Deployment.Application.ApplicationDeployment>
