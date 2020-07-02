---
title: Wdrażanie pakietów MSI i VSIX języka DSL
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d4de8d7560cb43115a30e29516e0e88b4d02d21
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542619"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Wdrażanie pakietów MSI i VSIX języka DSL
Język specyficzny dla domeny można zainstalować na własnym komputerze lub na innych komputerach. Program Visual Studio musi być już zainstalowany na komputerze docelowym.

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a>Wybieranie między wdrożeniem VSIX i MSI
 Istnieją dwie metody wdrażania języka specyficznego dla domeny:

|Metoda|Zalety|
|-|-|
|VSX (rozszerzenie programu Visual Studio)|Bardzo łatwe do wdrożenia: Skopiuj i wykonaj plik **. vsix** z projektu DslPackage.<br /><br /> Aby uzyskać więcej informacji, zobacz [Instalowanie i odinstalowywanie DSL przy użyciu VSX](#Installing).|
|MSI (plik Instalatora)|— Umożliwia użytkownikowi otwarcie programu Visual Studio przez dwukrotne kliknięcie pliku DSL.<br />— Kojarzy ikonę z typem pliku DSL na komputerze docelowym.<br />— Kojarzy XSD (schemat XML) z typem pliku DSL. Pozwala to uniknąć ostrzeżeń, gdy plik jest ładowany do programu Visual Studio.<br /><br /> Aby utworzyć plik MSI, należy dodać do swojego rozwiązania projekt instalacyjny.<br /><br /> Aby uzyskać więcej informacji, zobacz [wdrażanie DSL przy użyciu pliku MSI](#msi).|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a>Instalowanie i odinstalowywanie DSL przy użyciu VSX

Gdy linia DSL jest instalowana przez tę metodę, użytkownik może otworzyć plik DSL z poziomu programu Visual Studio, ale nie można otworzyć tego pliku z poziomu Eksploratora Windows.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>Aby zainstalować DSL przy użyciu VSX

1. Zlokalizuj plik **VSIX** , który został skompilowany przez projekt pakietu DSL:

   1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **DslPackage** , a następnie kliknij polecenie **Otwórz folder w Eksploratorze plików**.

   2. Znajdź plik ** \\ \* \\ bin**_YourProject_**. DslPackage. vsix**

2. Skopiuj plik **. vsix** do komputera docelowego, na którym chcesz zainstalować DSL. Może to być własny komputer lub inny.

   - Komputer docelowy musi mieć jedną z wersji programu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , która obsługuje językami DSL w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [obsługiwane wersje programu Visual Studio dla wizualizacji & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - Na komputerze docelowym musi znajdować się jedna z wersji programu Visual Studio określona w **DslPackage\source.Extensions.manifest**.

3. Na komputerze docelowym kliknij dwukrotnie plik **. vsix** .

    Zostanie otwarty **Instalator rozszerzenia programu Visual Studio** , który zainstaluje rozszerzenie.

4. Uruchom lub Uruchom ponownie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] .

5. Aby przetestować DSL, należy użyć programu Visual Studio do utworzenia nowego pliku, który ma rozszerzenie zdefiniowane dla DSL.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Aby odinstalować program DSL, który został zainstalowany przy użyciu VSX

1. W menu **Narzędzia** wybierz pozycję **rozszerzenia i aktualizacje**.

2. Rozwiń **zainstalowane rozszerzenia**.

3. Wybierz rozszerzenie, w którym zdefiniowano DSL, a następnie kliknij przycisk **Odinstaluj**.

   Rzadko błędne rozszerzenie nie zostanie załadowane i tworzy raport w oknie błędu, ale nie jest wyświetlany w Menedżerze rozszerzeń. W takim przypadku można usunąć rozszerzenie, usuwając plik z:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a>Wdrażanie języka DSL w pliku MSI
 Definiując plik MSI (Instalator Windows) dla DSL, można zezwolić użytkownikom na otwieranie plików DSL z poziomu Eksploratora Windows. Możesz również skojarzyć ikonę i Krótki opis z rozszerzeniem nazwy pliku. Ponadto MSI może zainstalować plik XSD, który może służyć do weryfikowania plików DSL. Jeśli chcesz, możesz dodać inne składniki do pliku MSI, który zostanie zainstalowany w tym samym czasie.

 Aby uzyskać więcej informacji o plikach MSI i innych opcjach wdrażania, zobacz [wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

 Aby skompilować plik MSI, należy dodać projekt konfiguracji do rozwiązania programu Visual Studio. Najprostszą metodą tworzenia projektu Instalatora jest użycie szablonu CreateMsiSetupProject.tt, który można pobrać z [witryny VMSDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

### <a name="to-deploy-a-dsl-in-an-msi"></a>Aby wdrożyć język DSL w pliku MSI

1. Ustaw `InstalledByMsi` w manifeście rozszerzenia. Zapobiega to instalowaniu i odinstalowywaniu VSX z wyjątkiem MSI. Jest to ważne, jeśli w pliku MSI zostaną uwzględnione inne składniki.

   1. Otwórz DslPackage\source.extension.tt

   2. Wstaw następujący wiersz przed `<SupportedProducts>` :

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Utwórz lub Edytuj ikonę, która będzie reprezentować język DSL w Eksploratorze Windows. Na przykład Edytuj **DslPackage\Resources\File.ico**

3. Upewnij się, że następujące atrybuty DSL są poprawne:

   - W Eksploratorze DSL kliknij węzeł główny, a w okno Właściwości Przejrzyj:

       - Opis

       - Wersja

   - Kliknij węzeł **Edytor** i w okno właściwości kliknij **ikonę**. Ustaw wartość, aby odwoływać się do pliku ikony w **DslPackage\Resources**, na przykład **plik. ico**

   - W menu **kompilacja** Otwórz **Configuration Manager**i wybierz konfigurację, którą chcesz skompilować, taką jak **wersja** lub **Debuguj**.

4. Przejdź do [strony głównej wizualizacji i modelowania SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db), a następnie na karcie **pliki do** pobrania Pobierz **CreateMsiSetupProject.tt**.

5. Dodaj **CreateMsiSetupProject.tt** do projektu DSL.

    Program Visual Studio utworzy plik o nazwie **CreateMsiSetupProject. VDPROJ**.

6. W Eksploratorze Windows skopiuj pozycję DSL \\ *. VDPROJ do nowego folderu o nazwie Setup.

    (Jeśli chcesz, możesz teraz wykluczyć CreateMsiSetupProject.tt z projektu DSL).

7. W **Eksplorator rozwiązań**należy dodać **Setup \\ \* . VDPROJ** jako istniejący projekt.

8. W menu **projekt** kliknij pozycję **zależności projektu**.

    W oknie dialogowym **zależności projektu** wybierz projekt Instalatora.

    Zaznacz pole obok **DslPackage**.

9. Ponownie skompiluj rozwiązanie.

10. W Eksploratorze Windows Znajdź utworzony plik MSI w projekcie Instalatora.

     Skopiuj plik MSI na komputer, na którym chcesz zainstalować DSL. Kliknij dwukrotnie plik MSI. Instalator zostanie uruchomiony.

11. Na komputerze docelowym Utwórz nowy plik, który ma rozszerzenie pliku DSL. Sprawdź, czy:

    - W widoku listy Eksploratora Windows zostanie wyświetlony plik z ikoną i opisem zdefiniowanym przez użytkownika.

    - Po dwukrotnym kliknięciu pliku zostanie uruchomiony program Visual Studio, a plik DSL zostanie otwarty w edytorze DSL.

    Jeśli wolisz, możesz utworzyć projekt instalacyjny ręcznie, zamiast używać szablonu tekstu. Aby zapoznać się z przewodnikiem zawierającym tę procedurę, zobacz rozdział 5 [laboratorium SDK wizualizacji i modelowania](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207).

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Aby odinstalować DSL, które zostały zainstalowane z pliku MSI

1. W systemie Windows otwórz Panel sterowania **programy i funkcje** .

2. Odinstaluj DSL.

3. Uruchom ponownie program Visual Studio.
