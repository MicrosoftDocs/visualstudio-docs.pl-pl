---
title: Wdrażanie pakietów MSI i VSIX przy użyciu języka DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4917fc81f439ef0185a753fb1c4c85e460eb7681
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297740"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Wdrażanie pakietów MSI i VSIX języka DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Język specyficzny dla domeny można zainstalować na własnym komputerze lub na innych komputerach. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] musi być już zainstalowana na komputerze docelowym.

## <a name="which"></a>Wybieranie między wdrożeniem VSIX i MSI
 Istnieją dwie metody wdrażania języka specyficznego dla domeny:

|Metoda|Korzyści|
|------------|--------------|
|VSX (rozszerzenie[!INCLUDE[vsprvs](../includes/vsprvs-md.md)])|Bardzo łatwe do wdrożenia: Skopiuj i wykonaj plik **. vsix** z projektu DslPackage.<br /><br /> Aby uzyskać więcej informacji, zobacz [Instalowanie i odinstalowywanie DSL przy użyciu VSX](#Installing).|
|MSI (plik Instalatora)|-Zezwala użytkownikowi na otwieranie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przez dwukrotne kliknięcie pliku DSL.<br />— Kojarzy ikonę z typem pliku DSL na komputerze docelowym.<br />— Kojarzy XSD (schemat XML) z typem pliku DSL. Pozwala to uniknąć ostrzeżeń, gdy plik jest ładowany do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].<br /><br /> Aby utworzyć plik MSI, należy dodać do swojego rozwiązania projekt instalacyjny.<br /><br /> Aby uzyskać więcej informacji, zobacz [wdrażanie DSL przy użyciu pliku MSI](#msi).|

## <a name="Installing"></a>Instalowanie i odinstalowywanie DSL przy użyciu VSX
 Po zainstalowaniu programu DSL przez tę metodę użytkownik może otworzyć plik DSL z poziomu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ale nie można otworzyć tego pliku z poziomu Eksploratora Windows.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Aby zainstalować DSL przy użyciu VSX

1. Na komputerze Znajdź plik **. vsix** , który został skompilowany przez projekt pakietu DSL.

    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **DslPackage** , a następnie kliknij polecenie **Otwórz folder w Eksploratorze Windows**.

    2. Znajdź **\\bin pliku \*\\** _YourProject_ **. DslPackage. vsix**

2. Skopiuj plik **. vsix** do komputera docelowego, na którym chcesz zainstalować DSL. Może to być własny komputer lub inny.

    - Na komputerze docelowym musi być zainstalowana jedna z następujących wersji programu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], która obsługuje językami DSL w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [obsługiwane wersje programu Visual Studio dla wizualizacji & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - Komputer docelowy musi mieć jedną z wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] określonych w **DslPackage\source.Extensions.manifest**.

3. Na komputerze docelowym kliknij dwukrotnie plik **. vsix** .

     Zostanie otwarty **Instalator rozszerzenia programu Visual Studio** , który zainstaluje rozszerzenie.

4. Uruchom lub Uruchom ponownie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

5. Aby przetestować DSL, użyj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aby utworzyć nowy plik, który ma rozszerzenie zdefiniowane dla DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Aby odinstalować program DSL, który został zainstalowany przy użyciu VSX

1. W menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń**.

2. Rozwiń **zainstalowane rozszerzenia**.

3. Wybierz rozszerzenie, w którym zdefiniowano DSL, a następnie kliknij przycisk **Odinstaluj**.

   Rzadko błędne rozszerzenie nie zostanie załadowane i tworzy raport w oknie błędu, ale nie jest wyświetlany w Menedżerze rozszerzeń. W takim przypadku można usunąć rozszerzenie, usuwając plik z:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a>Wdrażanie języka DSL w pliku MSI
 Definiując plik MSI (Instalator Windows) dla DSL, można zezwolić użytkownikom na otwieranie plików DSL z poziomu Eksploratora Windows. Możesz również skojarzyć ikonę i Krótki opis z rozszerzeniem nazwy pliku. Ponadto MSI może zainstalować plik XSD, który może służyć do weryfikowania plików DSL. Jeśli chcesz, możesz dodać inne składniki do pliku MSI, który zostanie zainstalowany w tym samym czasie.

 Aby uzyskać więcej informacji o plikach MSI i innych opcjach wdrażania, zobacz [wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

 Aby skompilować plik MSI, należy dodać projekt konfiguracji do rozwiązania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Najprostszą metodą tworzenia projektu Instalatora jest użycie szablonu CreateMsiSetupProject.tt, który można pobrać z [witryny VMSDK](https://go.microsoft.com/fwlink/?LinkID=186128).

#### <a name="to-deploy-a-dsl-in-an-msi"></a>Aby wdrożyć język DSL w pliku MSI

1. Ustaw `InstalledByMsi` w manifeście rozszerzenia. Zapobiega to instalowaniu i odinstalowywaniu VSX z wyjątkiem MSI. Jest to ważne, jeśli w pliku MSI zostaną uwzględnione inne składniki.

   1. Open DslPackage\source.extension.tt

   2. Wstaw następujący wiersz przed `<SupportedProducts>`:

       ```
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Utwórz lub Edytuj ikonę, która będzie reprezentować język DSL w Eksploratorze Windows. Na przykład Edytuj **DslPackage\Resources\File.ico**

3. Upewnij się, że następujące atrybuty DSL są poprawne:

   - W Eksploratorze DSL kliknij węzeł główny, a w okno Właściwości Przejrzyj:

       - Opis

       - Wersja

   - Kliknij węzeł **Edytor** i w okno właściwości kliknij **ikonę**. Ustaw wartość, aby odwoływać się do pliku ikony w **DslPackage\Resources**, na przykład **plik. ico**

   - W menu **kompilacja** Otwórz **Configuration Manager**i wybierz konfigurację, którą chcesz skompilować, taką jak **wersja** lub **Debuguj**.

4. Przejdź do [strony głównej wizualizacji i modelowania SDK](https://go.microsoft.com/fwlink/?LinkID=186128), a następnie na karcie **pliki do** pobrania Pobierz **CreateMsiSetupProject.tt**.

5. Dodaj **CreateMsiSetupProject.tt** do projektu DSL.

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utworzy plik o nazwie **CreateMsiSetupProject. VDPROJ**.

6. W Eksploratorze Windows skopiuj pozycję DSL\\*. VDPROJ do nowego folderu o nazwie Setup.

    (Jeśli chcesz, możesz teraz wykluczyć CreateMsiSetupProject.tt z projektu DSL).

7. W **Eksplorator rozwiązań**należy dodać **Instalatora\\\*. VDPROJ** jako istniejący projekt.

8. W menu **projekt** kliknij pozycję **zależności projektu**.

    W oknie dialogowym **zależności projektu** wybierz projekt Instalatora.

    Zaznacz pole obok **DslPackage**.

9. Ponownie skompiluj rozwiązanie.

10. W Eksploratorze Windows Znajdź utworzony plik MSI w projekcie Instalatora.

     Skopiuj plik MSI na komputer, na którym chcesz zainstalować DSL. Kliknij dwukrotnie plik MSI. Instalator zostanie uruchomiony.

11. Na komputerze docelowym Utwórz nowy plik, który ma rozszerzenie pliku DSL. Sprawdź, czy:

    - W widoku listy Eksploratora Windows zostanie wyświetlony plik z ikoną i opisem zdefiniowanym przez użytkownika.

    - Po dwukrotnym kliknięciu pliku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uruchamiany i otwiera plik DSL w edytorze DSL.

    Jeśli wolisz, możesz utworzyć projekt instalacyjny ręcznie, zamiast używać szablonu tekstu. Aby zapoznać się z przewodnikiem zawierającym tę procedurę, zobacz rozdział 5 [laboratorium SDK wizualizacji i modelowania](https://go.microsoft.com/fwlink/?LinkId=208878).

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Aby odinstalować DSL, które zostały zainstalowane z pliku MSI

1. W systemie Windows otwórz Panel sterowania **programy i funkcje** .

2. Odinstaluj DSL.

3. Uruchom ponownie program Visual Studio.
