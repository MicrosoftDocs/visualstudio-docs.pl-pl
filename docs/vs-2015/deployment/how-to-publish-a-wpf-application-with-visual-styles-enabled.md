---
title: 'Instrukcje: Publikowanie aplikacji WPF przy użyciu włączonej funkcji stylów wizualnych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e2eb9da0913b3ce77ea30fd58d5243d5a380d19f
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954469"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Instrukcje: Publikowanie aplikacji WPF przy użyciu włączonej funkcji stylów wizualnych

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Style wizualne Włącz wygląd wspólnych formantów, aby zmienić w zależności od motywu, wybierany przez użytkownika. Domyślnie style wizualne nie są włączone dla aplikacji Windows Presentation Foundation (WPF), więc należy włączyć je ręcznie. Włączanie stylów wizualnych dla aplikacji WPF i opublikować rozwiązanie spowoduje wystąpienie błędu. W tym temacie opisano sposób rozwiązania tego błędu, a proces publikowania aplikacji WPF przy użyciu włączonej funkcji stylów wizualnych. Aby uzyskać więcej informacji na temat funkcji stylów wizualnych zobacz [wizualne omówienie style](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Aby uzyskać więcej informacji na temat komunikatu o błędzie, zobacz [Rozwiązywanie problemów z określonymi błędami wdrożeń technologii ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).

 Aby naprawić błąd i opublikować rozwiązanie, należy wykonać następujące zadania:

- [Publikowanie rozwiązania bez włączonej funkcji stylów wizualnych](#BKMK_publishsolwovs).

- [Utwórz plik manifestu](#BKMK_CreateManifest).

- [Osadzanie pliku manifestu w pliku wykonywalnego opublikowane rozwiązania](#BKMK_embedmanifest).

- [Podpisywanie manifestów aplikacji i wdrożenia](#BKMK_signappdeplyman).

  Następnie można przenieść opublikowane pliki do lokalizacji, z którego chcesz zainstalować aplikację użytkownikom końcowym.

## <a name="BKMK_publishsolwovs"></a> Publikowanie rozwiązania bez włączonej funkcji stylów wizualnych

1. Upewnij się, że projekt nie ma włączonej funkcji stylów wizualnych. Najpierw sprawdź następujący kod XML manifestu pliku projektu. Następnie kod XML jest obecny, należy ująć XML przy użyciu znacznik komentarza.

     Style wizualne nie są włączone domyślnie.

    ```xml
    <dependency>
        <dependentAssembly>
          <assemblyIdentity
              type="win32"
              name="Microsoft.Windows.Common-Controls"
              version="6.0.0.0"
              processorArchitecture="*"
              publicKeyToken="6595b64144ccf1df"
              language="*" />
        </dependentAssembly>
      </dependency>
    ```

     Poniższe procedury pokazują, jak można otworzyć pliku manifestu skojarzony z projektem.

    **Aby otworzyć plik manifestu w projekcie Visual Basic**

    1. Na pasku menu wybierz **projektu**, _ProjectName_**właściwości**, gdzie *ProjectName* jest nazwą projektu WPF.

         Są wyświetlane na stronach właściwości projektu WPF.

    2. Na **aplikacji** kartę, wybrać **ustawienia Windows widoku**.

         Plik app.manifest zostanie otwarty w **Edytor kodu**.

    **Aby otworzyć plik manifestu w projekcie języka C#**

    1. Na pasku menu wybierz **projektu**, _ProjectName_**właściwości**, gdzie *ProjectName* jest nazwą projektu WPF.

         Są wyświetlane na stronach właściwości projektu WPF.

    2. Na **aplikacji** kartę, zwróć uwagę na nazwę, która jest wyświetlana w polu manifestu. Jest to nazwa manifestu, który jest skojarzony z projektem.

        > [!NOTE]
        > Jeśli **osadzania manifestu z ustawieniami domyślnymi** lub **tworzenie aplikacji bez manifestu** są wyświetlane w polu manifestu nie mają włączonej funkcji stylów wizualnych. Jeśli nazwa pliku manifestu zostanie wyświetlona w polu manifestu, przejdź do następnego kroku w tej procedurze.

    3. W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** ().

         Ten przycisk pokazuje wszystkie elementy projektu, w tym te, które zostały wykluczone, które zwykle są ukryte. Plik manifestu jest wyświetlany jako element projektu.

2. Twórz i Publikuj swoje rozwiązanie. Aby uzyskać więcej informacji o sposobie publikowania rozwiązania, zobacz [jak: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="BKMK_CreateManifest"></a> Utwórz plik manifestu

1. Wklej następujący kod XML do pliku Notatnika.

     Poniższy kod XML w tym artykule opisano zestaw, który zawiera formanty, które obsługują stylów wizualnych.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
     <asmv1:assembly manifestVersion="1.0"
         xmlns="urn:schemas-microsoft-com:asm.v1"
         xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
         xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <dependency>
        <dependentAssembly>
          <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="*"
            publicKeyToken="6595b64144ccf1df"
            language="*" />
        </dependentAssembly>
      </dependency>
    </asmv1:assembly>
    ```

2. W programie Notatnik, kliknij przycisk **pliku**, a następnie kliknij przycisk **Zapisz jako**.

3. W **Zapisz jako** dialogowym **Zapisz jako typ** listy rozwijanej wybierz **wszystkie pliki**.

4. W **nazwy pliku** polu, nadaj plikowi nazwę i Dołącz **.manifest** na końcu nazwy pliku. Na przykład: **themes.manifest**.

5. Wybierz **Przeglądaj foldery** przycisku, wybierz dowolny folder, a następnie kliknij **Zapisz**.

    > [!NOTE]
    > W pozostałych procedurach założono, że nazwa tego pliku jest **themes.manifest** i czy plik jest zapisywany w katalogu C:\temp na komputerze.

## <a name="BKMK_embedmanifest"></a> Osadzanie pliku manifestu w pliku wykonywalnego opublikowane rozwiązania

1. Otwórz **wiersz polecenia programu Visual Studio**.

    Aby uzyskać więcej informacji o sposobie otwierania **Visual Studio Command Prompt**, zobacz [wiersz polecenia](http://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219).

   > [!NOTE]
   > Pozostałe kroki zakładają następujące rozwiązania:
   >
   > - Nazwa rozwiązania jest **MyWPFProject**.
   > - Rozwiązanie znajduje się w następującym katalogu: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.
   >
   > - To rozwiązanie jest publikowane do następującego katalogu: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.
   > - Najnowszą wersję plików opublikowanej aplikacji znajduje się w następującym katalogu: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Nie trzeba używać nazwy lub lokalizacje katalogu opisanych powyżej. Nazwy i lokalizacje opisanych powyżej są używane tylko w celu zilustrowania kroki wymagane do publikowania rozwiązania.

2. W wierszu polecenia należy zmienić ścieżkę do katalogu, który zawiera najnowszą wersję plików opublikowanej aplikacji. Poniższy przykład pokazuje, w tym kroku.

   ```
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. W wierszu polecenia Uruchom następujące polecenie, aby osadzić pliku manifestu w pliku wykonywalnego aplikacji.

   ```
   mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy
   ```

## <a name="BKMK_signappdeplyman"></a> Podpisywanie manifestów aplikacji i wdrożenia

1. W wierszu polecenia Uruchom następujące polecenie, aby usunąć `.deploy` rozszerzenie z pliku wykonywalnego w bieżącym katalogu.

   ```
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > W tym przykładzie założono, że tylko jeden plik ma `.deploy` rozszerzenie pliku. Upewnij się, zmiana nazwy wszystkich plików w tym katalogu, które mają `.deploy` rozszerzenie pliku.

2. W wierszu polecenia Uruchom następujące polecenie, aby podpisać manifest aplikacji.

   ```
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > W tym przykładzie przyjęto założenie, podpisać manifest za pomocą `.pfx` pliku projektu. Jeśli nie są podpisywania manifestu, można pominąć `–cf` parametr, który jest używany w tym przykładzie. W przypadku podpisywania manifestu za pomocą certyfikatu, który wymaga hasła, podaj `–password` opcji (`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`).

3. W wierszu polecenia Uruchom następujące polecenie, aby dodać `.deploy` rozszerzenie nazwy pliku, którego nazwa została zmieniona w poprzednim kroku tej procedury.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > W tym przykładzie przyjęto założenie, że tylko jeden plik miał `.deploy` rozszerzenie pliku. Upewnij się, zmiana nazwy wszystkich plików w tym katalogu, który stracił `.deploy` rozszerzenie nazwy pliku.

4. W wierszu polecenia Uruchom następujące polecenie, aby podpisać manifest wdrożenia.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > W tym przykładzie przyjęto założenie, podpisać manifest za pomocą `.pfx` pliku projektu. Jeśli nie są podpisywania manifestu, można pominąć `–cf` parametr, który jest używany w tym przykładzie. W przypadku podpisywania manifestu za pomocą certyfikatu, który wymaga hasła, podaj `–password` opcji, jak w poniższym przykładzie:`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`.

   Po wykonaniu tych kroków można umieścić opublikowanych pliki do lokalizacji, z którego chcesz zainstalować aplikację użytkownikom końcowym. Jeśli zamierzasz często aktualizacji rozwiązania, można przenieść te polecenia do skryptu i uruchom skrypt na każdym publikowaniu nowej wersji.

## <a name="see-also"></a>Zobacz też

[Rozwiązywanie problemów z określonymi błędami wdrożeń technologii ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
[style wizualne omówienie](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)
[wiersz polecenia](http://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219)
