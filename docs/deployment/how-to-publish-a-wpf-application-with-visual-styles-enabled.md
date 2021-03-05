---
title: Publikowanie aplikacji WPF z włączonymi stylami wizualizacji
description: Dowiedz się, jak opublikować aplikację WPF z włączonymi stylami wizualnymi, co pozwala na zmianę wyglądu kontrolek w zależności od motywu wybranego przez użytkownika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 285d624debed6dc498e3d274af2839137b5094d1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171282"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Instrukcje: publikowanie aplikacji WPF z włączonymi stylami wizualizacji

Style wizualne umożliwiają zmianę wyglądu wspólnych kontrolek w zależności od motywu wybranego przez użytkownika. Domyślnie style wizualizacji nie są włączone dla aplikacji Windows Presentation Foundation (WPF), więc należy włączyć je ręcznie. Jednak włączenie stylów wizualnych dla aplikacji WPF, a następnie opublikowanie rozwiązania spowoduje wystąpienie błędu. W tym temacie opisano sposób rozwiązania tego błędu i procesu publikowania aplikacji WPF z włączonymi stylami wizualizacji. Aby uzyskać więcej informacji na temat stylów wizualizacji, zobacz [Omówienie stylów wizualnych](/windows/desktop/Controls/visual-styles-overview). Aby uzyskać więcej informacji o komunikacie o błędzie, zobacz [Rozwiązywanie określonych błędów we wdrożeniach technologii ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).

 Aby rozwiązać ten problem i opublikować rozwiązanie, należy wykonać następujące zadania:

- [Publikuj rozwiązanie bez włączonych stylów wizualnych](#publish-the-solution-without-visual-styles-enabled).

- [Utwórz plik manifestu](#create-a-manifest-file).

- [Osadź plik manifestu w pliku wykonywalnym opublikowanego rozwiązania](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution).

- [Podpisywanie aplikacji i manifestów wdrożenia](#sign-the-application-and-deployment-manifests).

  Następnie można przenieść opublikowane pliki do lokalizacji, z której użytkownicy końcowi mają instalować aplikację.

## <a name="publish-the-solution-without-visual-styles-enabled"></a>Publikuj rozwiązanie bez włączonych stylów wizualnych

1. Upewnij się, że projekt nie ma włączonych stylów wizualnych. Najpierw sprawdź plik manifestu projektu dla poniższego kodu XML. Następnie, jeśli plik XML jest obecny, ujmij plik XML z tagiem komentarza.

     Domyślnie style wizualizacji nie są włączone.

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     W poniższych procedurach pokazano, jak otworzyć plik manifestu skojarzony z projektem.

    **Aby otworzyć plik manifestu w projekcie Visual Basic**

    1. Na pasku menu wybierz **projekt**, **Właściwości** *ProjectName* , gdzie *ProjectName* jest nazwą projektu WPF.

         Pojawią się strony właściwości projektu WPF.

    2. Na karcie **aplikacja** wybierz pozycję **Wyświetl ustawienia systemu Windows**.

         Plik App. manifest zostanie otwarty w **edytorze kodu**.

    **Aby otworzyć plik manifestu w projekcie C#**

    1. Na pasku menu wybierz **projekt**, **Właściwości** *ProjectName* , gdzie *ProjectName* jest nazwą projektu WPF.

         Pojawią się strony właściwości projektu WPF.

    2. Na karcie **aplikacja** Zanotuj nazwę, która pojawia się w polu manifest. To jest nazwa manifestu, który jest skojarzony z projektem.

        > [!NOTE]
        > W przypadku **osadzenia manifestu z ustawieniami domyślnymi** lub **Utwórz aplikację bez manifestu** pojawia się w polu manifestu, style wizualizacji nie są włączone. Jeśli nazwa pliku manifestu pojawia się w polu manifestu, przejdź do następnego kroku w tej procedurze.

    3. W **Eksplorator rozwiązań** wybierz opcję **Pokaż wszystkie pliki**.

         Ten przycisk pokazuje wszystkie elementy projektu, w tym te, które zostały wykluczone i te, które są zwykle ukryte. Plik manifestu jest wyświetlany jako element projektu.

2. Kompiluj i Publikuj rozwiązanie. Aby uzyskać więcej informacji o sposobach publikowania rozwiązania, zobacz [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="create-a-manifest-file"></a>Utwórz plik manifestu

1. Wklej następujący kod XML do pliku Notatnik.

     Ten plik XML opisuje zestaw zawierający kontrolki, które obsługują style wizualne.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <asmv1:assembly manifestVersion="1.0"
        xmlns="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dependency>
            <dependentAssembly>
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```

2. W Notatnik kliknij **plik**, a następnie kliknij przycisk **Zapisz jako**.

3. W oknie dialogowym **Zapisz jako** na liście rozwijanej **Zapisz jako typ** wybierz pozycję **wszystkie pliki**.

4. W polu **Nazwa pliku** Nazwij plik i Dołącz *. manifest* na końcu nazwy pliku. Na przykład: *motywy. manifest*.

5. Wybierz przycisk **Przeglądaj foldery** , wybierz dowolny folder, a następnie kliknij przycisk **Zapisz**.

    > [!NOTE]
    > Pozostałe procedury założono, że nazwa tego pliku to *motywy. manifest* , a plik jest zapisywany w katalogu *C:\Temp* na komputerze.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>Osadź plik manifestu w pliku wykonywalnym opublikowanego rozwiązania

1. Otwórz **wiersz polecenia dla deweloperów dla programu Visual Studio**.

    Aby uzyskać więcej informacji na temat otwierania wiersz polecenia dla deweloperów dla programu Visual Studio, zobacz [wiersz polecenia dla deweloperów i Developer PowerShell](../ide/reference/command-prompt-powershell.md).

   > [!NOTE]
   > Pozostałe kroki dotyczą następujących założeń rozwiązania:
   >
   > - Nazwa rozwiązania to **MyWPFProject**.
   > - Rozwiązanie znajduje się w następującym katalogu: `%UserProfile%\Documents\Visual Studio 2010\Projects\` .
   >
   > - Rozwiązanie jest publikowane w następującym katalogu: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` .
   > - Najnowsza wersja opublikowanych plików aplikacji znajduje się w następującym katalogu: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Nie trzeba używać nazwy ani lokalizacji katalogów opisanych powyżej. Nazwy i lokalizacje opisane powyżej są używane tylko w celu zilustrowania kroków wymaganych do opublikowania rozwiązania.

2. W wierszu polecenia Zmień ścieżkę do katalogu, który zawiera najnowszą wersję opublikowanych plików aplikacji. Poniższy przykład ilustruje ten krok.

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. W wierszu polecenia Uruchom następujące polecenie, aby osadzić plik manifestu w pliku wykonywalnym aplikacji.

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>Podpisywanie aplikacji i manifestów wdrożenia

1. W wierszu polecenia Uruchom następujące polecenie, aby usunąć rozszerzenie *. deploy* z pliku wykonywalnego w bieżącym katalogu.

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > W tym przykładzie przyjęto założenie, że tylko jeden plik ma rozszerzenie *. deploy* . Upewnij się, że zmieniono nazwę wszystkich plików w tym katalogu, które mają rozszerzenie *. deploy* .

2. W wierszu polecenia Uruchom następujące polecenie, aby podpisać manifest aplikacji.

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > W tym przykładzie przyjęto założenie, że manifest jest podpisywany przy użyciu pliku *PFX* projektu. Jeśli nie podpiszesz manifestu, możesz pominąć `-cf` parametr, który jest używany w tym przykładzie. W przypadku podpisywania manifestu przy użyciu certyfikatu, który wymaga hasła, należy określić `-password` opcję ( `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` ).

3. W wierszu polecenia Uruchom następujące polecenie, aby dodać rozszerzenie *. deploy* do nazwy pliku, którego nazwę zmieniono w poprzednim kroku tej procedury.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > W tym przykładzie przyjęto założenie, że tylko jeden plik miał rozszerzenie *. deploy* . Upewnij się, że zmieniono nazwę wszystkich plików w tym katalogu, które wcześniej miały rozszerzenie nazwy pliku *. deploy* .

4. W wierszu polecenia Uruchom następujące polecenie, aby podpisać manifest wdrożenia.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > W tym przykładzie przyjęto założenie, że manifest jest podpisywany przy użyciu pliku *PFX* projektu. Jeśli nie podpiszesz manifestu, możesz pominąć `-cf` parametr, który jest używany w tym przykładzie. W przypadku podpisywania manifestu przy użyciu certyfikatu, który wymaga hasła, określ `-password` opcję, jak w poniższym przykładzie: `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` .

   Po wykonaniu tych kroków można przenieść opublikowane pliki do lokalizacji, z której użytkownicy końcowi mają instalować aplikację. Jeśli zamierzasz zaktualizować rozwiązanie często, możesz przenieść te polecenia do skryptu i uruchomić skrypt przy każdym opublikowaniu nowej wersji.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z określonymi błędami wdrożeń technologii ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Przegląd stylów wizualnych](/windows/desktop/Controls/visual-styles-overview)
- [Włączanie stylów wizualnych](/windows/desktop/Controls/cookbook-overview)
- [wiersz polecenia dla deweloperów i deweloper programu PowerShell](../ide/reference/command-prompt-powershell.md)
