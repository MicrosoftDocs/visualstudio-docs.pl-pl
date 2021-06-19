---
title: Wdrażanie pakietów MSI i VSIX języka DSL
description: Dowiedz się, jak zainstalować język specyficzny dla domeny (DSL) na własnym komputerze lub na innych komputerach.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 879028746eac10160492f03651ef8b51714e9c6a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391013"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Wdrażanie pakietów MSI i VSIX języka DSL
Język specyficzny dla domeny można zainstalować na własnym komputerze lub na innych komputerach. Visual Studio musi być już zainstalowany na komputerze docelowym.

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a> Wybieranie między wdrożeniem VSIX i MSI
 Istnieją dwie metody wdrażania języka specyficznego dla domeny:

|Metoda|Korzyści|
|-|-|
|VSX (rozszerzenie Visual Studio)|Bardzo łatwe do wdrożenia: skopiuj i wykonaj **plik vsix** z projektu DslPackage.<br /><br /> Aby uzyskać więcej informacji, [zobacz Instalowanie i odinstalowywanie DSL przy użyciu VSX](#Installing).|
|MSI (plik instalatora)|- Umożliwia użytkownikowi otwieranie Visual Studio przez dwukrotne kliknięcie pliku DSL.<br />- Kojarzy ikonę z typem pliku DSL na komputerze docelowym.<br />- Kojarzy XSD (schemat XML) z typem pliku DSL. Pozwala to uniknąć ostrzeżeń podczas ładowania pliku do Visual Studio.<br /><br /> Aby utworzyć msi, należy dodać projekt instalacyjny do rozwiązania.<br /><br /> Aby uzyskać więcej informacji, zobacz [Deploying a DSL by using an MSI file (Wdrażanie DSL przy użyciu pliku MSI).](#msi)|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> Instalowanie i odinstalowywanie DSL przy użyciu VSX

Po zainstalowaniu DSL za pomocą tej metody, użytkownik może otworzyć plik DSL z poziomu Visual Studio, ale nie można otworzyć pliku z Eksplorator Windows.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>Aby zainstalować DSL przy użyciu VSX

1. Znajdź plik **vsix,** który został sbudowaną przez projekt pakietu DSL:

   1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **DslPackage,** a następnie kliknij polecenie **Otwórz folder w Eksplorator plików**.

   2. Znajdź plik **\\ \* \\ bin**_YourProject_**. DslPackage.vsix**

2. Skopiuj plik **vsix** na komputer docelowy, na którym chcesz zainstalować DSL. Może to być Twój własny komputer lub inny.

   - Komputer docelowy musi mieć jedną z wersji programu , która obsługuje pliki [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] DSL w czasie działania. Aby uzyskać więcej informacji, zobacz [Supported Visual Studio Editions for Visualization & Modeling SDK (Obsługiwane](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)wersje & SDK modelowania wizualizacji).

   - Na komputerze docelowym musi być określona jedna z wersji Visual Studio **DslPackage\source.extensions.manifest.**

3. Na komputerze docelowym kliknij dwukrotnie plik **vsix.**

    **Visual Studio zostanie** otwarty Instalator rozszerzenia i zainstaluje rozszerzenie.

4. Uruchom lub uruchom ponownie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] program .

5. Aby przetestować DSL, użyj Visual Studio, aby utworzyć nowy plik z rozszerzeniem zdefiniowanym dla DSL.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Aby odinstalować DSL, który został zainstalowany przy użyciu vsx

1. W menu **Narzędzia** wybierz pozycję **Rozszerzenia i aktualizacje.**

2. Rozwiń **węzło zainstalowane rozszerzenia**.

3. Wybierz rozszerzenie, w którym zdefiniowano DSL, a następnie kliknij przycisk **Odinstaluj**.

   Rzadko nie można załadować uszkodzonego rozszerzenia i tworzy raport w oknie błędu, ale nie jest wyświetlany w Menedżerze rozszerzeń. W takim przypadku możesz usunąć rozszerzenie, usuwając plik z:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a> Wdrażanie DSL w msi
 Definiując plik MSI (Instalator Windows) dla DSL, można zezwolić użytkownikom na otwieranie plików DSL z Eksplorator Windows. Możesz również skojarzyć ikonę i krótki opis z rozszerzeniem nazwy pliku. Ponadto plik MSI może zainstalować XSD, który może służyć do weryfikowania plików DSL. Jeśli chcesz, możesz dodać do msi inne składniki, które zostaną zainstalowane w tym samym czasie.

 Aby uzyskać więcej informacji na temat plików MSI i innych opcji wdrażania, zobacz [Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

 Aby utworzyć instalator MSI, należy dodać projekt Instalatora do Visual Studio rozwiązania. Najprostszą metodą tworzenia projektu instalatora jest użycie szablonu CreateMsiSetupProject.tt, który można pobrać z witryny [zestawu VMSDK.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

### <a name="to-deploy-a-dsl-in-an-msi"></a>Aby wdrożyć DSL w MSI

1. Ustaw `InstalledByMsi` w manifeście rozszerzenia. Zapobiega to instalowaniu i odinstalowywaniu programu VSX z wyjątkiem pakietu MSI. Jest to ważne w przypadku dołączania innych składników do msi.

   1. Otwórz pakiet DslPackage\source.extension.tt

   2. Wstaw następujący wiersz przed `<SupportedProducts>` :

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Utwórz lub edytuj ikonę, która będzie reprezentować DSL w Eksplorator Windows. Na przykład edytuj **plik DslPackage\Resources\File.ico**

3. Upewnij się, że następujące atrybuty DSL są poprawne:

   - W Eksploratorze DSL kliknij węzeł główny, a następnie okno Właściwości przejrzyj:

       - Opis

       - Wersja

   - Kliknij węzeł **Edytor,** a następnie w okno Właściwości kliknij pozycję **Ikona**. Ustaw wartość , aby odwoływać się do pliku ikony w **pliku DslPackage\Resources,** na przykład **File.ico**

   - W menu **Build (Kompilacja)** otwórz **Menedżer konfiguracji**, a następnie wybierz konfigurację, którą chcesz skompilować, na przykład Release **(Wydanie) lub** Debug **(Debugowanie).**

4. Przejdź do [strony głównej zestawu SDK wizualizacji](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)i modelowania, a następnie na karcie **Pliki** do pobrania **pobierz CreateMsiSetupProject.tt**.

5. Dodaj **CreateMsiSetupProject.tt** projektu DSL.

    Visual Studio utworzy plik o nazwie **CreateMsiSetupProject.vdproj.**

6. W Eksplorator Windows skopiuj plik Dsl \\ *.vdproj do nowego folderu o nazwie Setup (Konfiguracja).

    (Jeśli chcesz, możesz teraz wykluczyć CreateMsiSetupProject.tt z projektu DSL).

7. W **Eksplorator rozwiązań** dodaj **plik \\ \* vdproj Instalatora** jako istniejący projekt.

8. W menu **Project** (Projekt) kliknij pozycję **Project Dependencies (Zależności projektu).**

    W **oknie dialogowym** Zależności projektu wybierz projekt konfiguracji.

    Zaznacz pole wyboru obok pola **DslPackage**.

9. Ponownie skompiluj rozwiązanie.

10. W Eksplorator Windows pliku MSI znajdź go w projekcie instalatora.

     Skopiuj plik MSI na komputer, na którym chcesz zainstalować DSL. Kliknij dwukrotnie plik MSI. Zostanie uruchomiony instalator.

11. Na komputerze docelowym utwórz nowy plik z rozszerzeniem pliku DSL. Sprawdź, czy:

    - W Eksplorator Windows listy zostanie wyświetlony plik ze zdefiniowaną ikoną i opisem.

    - Dwukrotne kliknięcie pliku spowoduje Visual Studio i otwarcie pliku DSL w edytorze DSL.

    Jeśli wolisz, możesz utworzyć projekt Instalatora ręcznie, zamiast korzystać z szablonu tekstowego. Aby uzyskać przewodnik, który zawiera tę procedurę, zobacz Rozdział 5 laboratorium zestawu [SDK wizualizacji i modelowania.](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207)

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Aby odinstalować DSL, który został zainstalowany z msi

1. W systemie Windows otwórz **panel sterowania Programy i** funkcje.

2. Odinstaluj DSL.

3. Uruchom ponownie program Visual Studio.
