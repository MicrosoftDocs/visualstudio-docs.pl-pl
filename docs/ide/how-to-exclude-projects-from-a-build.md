---
title: 'Instrukcje: Wykluczanie projektów z kompilacji'
description: Dowiedz się, jak za pomocą programu Visual Studio skompilować rozwiązanie bez kompilowania wszystkich projektów, które zawiera.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b0e164c24770048495d16da852523b3dd50a43a
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136904"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Instrukcje: Wykluczanie projektów z kompilacji

Możesz skompilować rozwiązanie bez kompilowania wszystkich projektów, które zawiera. Na przykład można wykluczyć projekt, który przerywa kompilację. Następnie można skompilować projekt po zbadaniu i rozpoczęciu problemów.

Możesz wykluczyć projekt, wykonując następujące podejścia:

- Tymczasowe usunięcie z aktywnej konfiguracji rozwiązania.

- Tworzenie konfiguracji rozwiązania, która nie zawiera projektu.

Aby uzyskać więcej informacji, zobacz [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Aby tymczasowo usunąć projekt z aktywnej konfiguracji rozwiązania

1. Na pasku menu wybierz kolejno opcje **Kompiluj**  >  **Configuration Manager**.

2. W tabeli **kontekstowe projektu** Znajdź projekt, który ma zostać wykluczony z kompilacji.

3. W kolumnie **kompilacja** dla projektu wyczyść pole wyboru.

4. Wybierz przycisk **Zamknij** , a następnie Skompiluj ponownie rozwiązanie.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Aby utworzyć konfigurację rozwiązania, która wyklucza projekt

1. Na pasku menu wybierz kolejno opcje **Kompiluj**  >  **Configuration Manager**.

2. Na liście **Konfiguracja aktywnego rozwiązania** wybierz opcję **\<New>** .

3. W polu **Nazwa** wprowadź nazwę konfiguracji rozwiązania.

4. Z listy **Kopiuj ustawienia z** wybierz konfigurację rozwiązania, dla której chcesz utworzyć nową konfigurację (na przykład **debugowanie**), a następnie wybierz przycisk **OK** .

5. W oknie dialogowym **Configuration Manager** wyczyść pole wyboru w kolumnie **kompilacja** dla projektu, który ma zostać wykluczony, a następnie wybierz przycisk **Zamknij** .

6. Na pasku narzędzi **Standardowy** Sprawdź, czy nowa konfiguracja rozwiązania jest aktywna konfiguracja w polu **konfiguracje rozwiązania** .

7. Na pasku menu wybierz kolejno opcje **Kompiluj**  >  **Kompiluj ponownie rozwiązanie**.

## <a name="skipped-projects"></a>Pominięte projekty

Projekty można pominąć podczas kompilacji, ponieważ nie są aktualne lub są wykluczone z konfiguracji. Program Visual Studio używa programu MSBuild do kompilowania projektów. MSBuild kompiluje tylko element docelowy, jeśli dane wyjściowe są starsze niż dane wejściowe, zgodnie z sygnaturami czasowymi plików. Aby wymusić ponowną **kompilację**, użyj polecenia Skompiluj  >  **skompilować ponownie rozwiązanie**.

W okienku **kompilacja** okna **dane wyjściowe** program Visual Studio zgłasza liczbę projektów, które były aktualne, liczbę, która została utworzona pomyślnie, liczbę, która się nie powiodła, oraz liczbę, która została pominięta. Liczba pominiętych nie obejmuje projektów, które nie zostały skompilowane, ponieważ były aktualne. Gdy projekty są wykluczone z aktywnej konfiguracji, są pomijane podczas kompilacji. W danych wyjściowych kompilacji zobaczysz komunikat wskazujący, że projekt został pominięty:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Aby dowiedzieć się, dlaczego projekt został pominięty, zanotuj aktywną konfigurację ( `Debug x86` w poprzednim przykładzie) i wybierz opcję **Kompiluj**  >  **Configuration Manager**. Można wyświetlić lub zmienić, które projekty są pomijane dla każdej konfiguracji, zgodnie z opisem w tym artykule.

## <a name="see-also"></a>Zobacz też

- [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)
- [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Instrukcje: kompilowanie wielu konfiguracji jednocześnie](../ide/how-to-build-multiple-configurations-simultaneously.md)
