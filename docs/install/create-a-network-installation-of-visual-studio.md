---
title: Utworzenie instalacji sieciowej
description: Dowiedz się, jak utworzyć punkt instalacji sieciowej dla wdrażania programu Visual Studio w przedsiębiorstwie.
ms.date: 02/27/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 63fad9e14bba478d2e0f2a69c42de18f45156482
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324292"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Tworzenie instalacji sieciowej programu Visual Studio

Zazwyczaj administrator przedsiębiorstwa tworzy punkt instalacji sieci do wdrożenia na klienckich stacjach roboczych. Zaprojektowaliśmy programu Visual Studio 2017 umożliwia buforowanie plików dla początkowej instalacji oraz wszystkie aktualizacje produktu na pojedynczy folder. (Ten proces jest również określany jako _tworzenie układu_.) 

Firma Microsoft wykonane to dlatego, że stacje robocze klienta można użyć tej samej lokalizacji sieci do zarządzania ich instalacji, nawet jeśli ich jeszcze nie zostało zaktualizowane do obsługi najnowszej aktualizacji.

 > [!NOTE]
 > Jeśli masz wiele wersji programu Visual Studio używane w przedsiębiorstwie (na przykład program Visual Studio Professional i Visual Studio Enterprise), należy utworzyć udział instalacji oddzielnej sieci dla każdej wersji.

## <a name="download-the-visual-studio-bootstrapper"></a>Pobierz program inicjujący programu Visual Studio

Pobierz wersję Visual Studio, które chcesz. Upewnij się, że kliknij **Zapisz**, a następnie kliknij przycisk **Otwórz folder**.

Ustawienia pliku wykonywalnego&mdash;lub dokładniej, plik inicjujący&mdash;musi odpowiadać jednej z następujących czynności.

|Wersja | Pobieranie|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Community | [**vs_community.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |

Inne obsługiwane programów inicjujących obejmują [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe), i [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Utwórz folder instalacji w trybie offline

Musi mieć połączenie internetowe, aby ukończyć ten krok. Aby utworzyć instalacji w trybie offline z wszystkich języków i wszystkie funkcje, użyj jednej z poleceń z poniższych przykładów.

   > [!IMPORTANT]
   > Pełny układ programu Visual Studio 2017 wymaga co najmniej 35 GB miejsca na dysku i może zająć trochę czasu, aby pobrać.  Zobacz [Dostosowywanie układu sieci](#customize-the-network-layout) sekcji, aby uzyskać szczegółowe informacje na temat sposobu tworzenia układu z wyłącznie te składniki, które chcesz zainstalować.
   >
   > [!TIP]
   > Upewnij się, uruchom polecenie z katalogu pobierania. Zwykle to `C:\Users\<username>\Downloads` na komputerze z systemem Windows 10.

- For Visual Studio Enterprise, run:

  ```vs_enterprise.exe --layout c:\vs2017offline```

- Dla programu Visual Studio Professional Uruchom polecenie:

  ```vs_professional.exe --layout c:\vs2017offline```

- For Visual Studio Community, run:

  ```vs_community.exe --layout c:\vs2017offline```

## <a name="modify-the-responsejson-file"></a>Zmodyfikuj plik response.json

Można zmodyfikować response.json, aby ustawić wartości domyślne, które są używane po uruchomieniu Instalatora.  Na przykład, można skonfigurować `response.json` pliku, aby wybrać określony zbiór obciążeń wybrana automatycznie.
Zobacz [instalacji automatyzacji programu Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md) Aby uzyskać szczegółowe informacje.

## <a name="copy-the-layout-to-a-network-share"></a>Skopiować układ do udziału sieciowego

Hosta układu w udziale sieciowym, dzięki czemu może działać z innych komputerów.

Przykład:

```cmd
xcopy /e c:\vs2017offline \\server\products\VS2017
```

## <a name="customize-the-network-layout"></a>Dostosowywanie układu sieci

Istnieje kilka opcji, których można użyć w celu dostosowania układu sieci. Można utworzyć częściowe układ, który zawiera tylko określony zbiór [ustawień regionalnych języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [obciążeń, składniki i ich zależności zalecane lub opcjonalne](workload-and-component-ids.md). Może to być przydatne, jeśli wiesz, że zamierzasz wdrożyć podzbiorem obciążeń na klienckich stacjach roboczych. Typowe parametry wiersza polecenia dla dostosowywania układu obejmują:

* `--add` Aby określić [obciążenia lub składnika ID](workload-and-component-ids.md). <br>Jeśli `--add` jest używany, te obciążenia i składniki określony za pomocą `--add` zostaną pobrane.  Jeśli `--add` jest nie używane wszystkie obciążenia i składniki zostaną pobrane.
* `--includeRecommended` Aby uwzględnić wszystkie składniki zalecane dla określonego obciążenia identyfikatorów
* `--includeOptional` Aby uwzględnić wszystkie składniki zalecanych i opcjonalnych dla określonego obciążenia identyfikatorów.
* `--lang` Aby określić [ustawień regionalnych języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Poniżej przedstawiono kilka przykładów sposobu tworzenia niestandardowego układu częściowe.

* Aby pobrać wszystkie obciążenia i składniki dla tylko jednego języka, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```

* Aby pobrać wszystkie obciążenia i składniki dla wielu języków, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP
    ```

* Aby pobrać jeden obciążenia dla wszystkich języków, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Aby pobrać dwóch obciążeń i jeden składnik opcjonalny w trzech językach, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Aby pobrać dwóch obciążeń i wszystkie jego zalecane składniki:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended 
    ```

* Aby pobrać dwóch obciążeń i wszystkie ich zalecanych i opcjonalnych składników, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional 
    ```

### <a name="new-in-version-153"></a>Nowość w wersji 15.3

Po uruchomieniu polecenia układ, opcje, które określisz są zapisywane (na przykład obciążeń i języków). Układ kolejnych poleceń będzie zawierać wszystkie poprzednie opcje.  Poniżej przedstawiono przykład układu z jednego obciążeniem dla języka angielskiego tylko:

```cmd
vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Jeśli chcesz zaktualizować ten układ do nowszej wersji, nie trzeba określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia są zapisywane i używane przez dowolne polecenia kolejnych układu, w tym folderze układu.  Następujące polecenie spowoduje zaktualizowanie istniejących układ częściowe.

```cmd
vs_enterprise.exe --layout c:\VS2017Layout
```

Jeśli chcesz dodać dodatkowe obciążenia, tutaj przykładowy sposób to zrobić. W tym przypadku dodamy obciążenie platformy Azure i zlokalizowanego języka.  Teraz zarządzane pulpitu i platformy Azure znajdują się w tym układzie.  Zasoby język angielski i niemiecki są obejmują dla tych obciążeń. Układ jest aktualizowane do najnowszej dostępnej wersji.

```cmd
vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Aby zaktualizować istniejący układ pełny układ, należy użyć wszystkich opcji, jak pokazano w poniższym przykładzie.

```cmd
vs_enterprise.exe --layout c:\VS2017Layout --all
```

## <a name="deploy-from-a-network-installation"></a>Wdrażanie z instalacji sieciowej

Administratorzy mogą wdrożyć Visual Studio na klienckich stacjach roboczych w skrypcie instalacji. Lub użytkowników, którzy mają uprawnienia administratora, można uruchomić Instalatora bezpośrednio z poziomu udziału, aby zainstalować program Visual Studio na swojej maszynie.

* Użytkownicy mogą zainstalować, uruchamiając następujące polecenie: <br>
    ```cmd
    \\server\products\VS2017\vs_enterprise.exe
    ```

* Administratorzy mogą instalować w trybie nienadzorowanym, uruchamiając następujące polecenie:
    ```cmd
    \server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Aby uniknąć błąd, upewnij się, że Twoje pełną ścieżkę instalacji jest mniejszy niż 80 znaków.
>
> [!TIP]
> Gdy wykonywane w ramach pliku wsadowego `--wait` opcji zapewnia, że `vs_enterprise.exe` proces będzie czekał instalacja została zakończona, zanim zwraca kod zakończenia.<br><br>Jest to przydatne, jeśli administrator przedsiębiorstwa chce, aby wykonać dalsze czynności na Zakończono instalowanie (na przykład, aby [zastosować klucz produktu do pomyślnej instalacji](automatically-apply-product-keys-when-deploying-visual-studio.md)), ale musi czekać na zakończenie obsługi instalacji Zwrócony kod z tej instalacji.<br><br>Jeśli nie używasz `--wait`, `vs_enterprise.exe` proces kończy się przed instalacja została zakończona i zwraca kod zakończenia niedokładne, która nie zawiera stanu operacji instalacji.

Podczas instalacji z układu, zawartość, która jest zainstalowana jest uzyskiwany z układu. Jednak jeśli wybierzesz składnik, który nie znajduje się w układzie, będzie można pobrać z Internetu.  Jeśli chcesz uniemożliwić pobranie żadnej zawartości, których brakuje w układzie, użyj Instalatora programu Visual Studio `--noWeb` opcji. Jeśli `--noWeb` jest używany i układu nie ma żadnej zawartości, który został wybrany do zainstalowania, Instalator zakończy się niepowodzeniem.

> [!IMPORTANT]
> `--noWeb` Opcji nie zatrzymuje instalację programu Visual Studio z sprawdzania dostępności aktualizacji. Aby uzyskać więcej informacji, zobacz [kontrolowania aktualizacji z wdrożeniami programu Visual Studio sieciowymi programami wykorzystującymi](controlling-updates-to-visual-studio-deployments.md) strony.

### <a name="error-codes"></a>Kody błędów

Jeśli użyto `--wait` parametru, a następnie w zależności od wyniku operacji, `%ERRORLEVEL%` zmienna środowiskowa jest ustawiony na jedną z następujących wartości:

  | **Wartość** | **wynik** |
  | --------- | ---------- |
  | 0 | Operacja została ukończona pomyślnie |
  | 3010 | Operacja ukończona pomyślnie, ale instalacja wymaga ponownego uruchomienia, zanim będzie można jej używać. |
  | Inne | Wystąpił błąd warunek — Sprawdź dzienniki Aby uzyskać więcej informacji |

## <a name="update-a-network-install-layout"></a>Aktualizowanie układu instalacji sieciowej

Podczas aktualizacji produktów są dostępne, może okazać się konieczne [aktualizowanie układu instalacji sieciowej](update-a-network-installation-of-visual-studio.md) zestawowi zaktualizowane pakiety.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Jak utworzyć układ dla poprzedniej wersji programu Visual Studio 2017

> [!NOTE]
> Programów inicjujących w programie Visual Studio 2017, które są dostępne na [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) pobranie i zainstalowanie najnowszej wersji programu Visual Studio 2017, który jest dostępny zawsze, gdy są uruchamiane.<br><br>Dlatego możesz pobrać program Visual Studio *programu inicjującego* już dziś i uruchom go sześciu miesięcy od teraz, instaluje wersję programu Visual Studio 2017, która jest aktualne w momencie, uruchom program inicjujący.<br><br>Jednak jeśli tworzysz *układ* i zainstaluj go z niej, układ instaluje określoną wersję programu Visual Studio, który istnieje w układzie. Mimo że nowszej wersji może istnieć w trybie online, otrzymasz wersji programu Visual Studio, który jest w układzie.

Jeśli musisz utworzyć układ dla starszej wersji programu Visual Studio 2017, przejdź do strony [ https://my.visualstudio.com ](https://my.visualstudio.com) do pobrania "stały" wersje programów inicjujących programu Visual Studio 2017.

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak uzyskać pomoc techniczną dla Instalatora w trybie offline

Jeśli wystąpi problem z instalacją w trybie offline, chcielibyśmy się dowiedzieć o nim. Najlepszym sposobem, aby przekazać nam polega na użyciu [Zgłoś Problem](../ide/how-to-report-a-problem-with-visual-studio.md) narzędzia. Korzystając z tego narzędzia, możesz wysłać nam telemetrii i dzienniki, musimy pomóc nam zdiagnozować i rozwiązać problem.

Oferujemy również [ **Czat na żywo** ](https://visualstudio.microsoft.com/vs/support/#talktous) opcję pomocy technicznej (tylko język angielski) w przypadku problemów związanych z instalacją.

Inne opcje pomocy technicznej dostępne, mamy zbyt. Aby uzyskać listę, zobacz nasze [Porozmawiaj z nami](../ide/talk-to-us.md) strony.

## <a name="see-also"></a>Zobacz także

* [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Sterowanie aktualizacjami na potrzeby wdrożenia oparte na sieci programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
