---
title: 'Instrukcje: Wykluczanie projektów z kompilacji'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54e65c411afe9815696112dfbcc99bcb9433c4db
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416865"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Instrukcje: Wykluczanie projektów z kompilacji

Możesz skompilować rozwiązanie bez kompilowania wszystkich projektów, które zawiera. Na przykład można wykluczyć projekt, który przerywa kompilację. Następnie można skompilować projekt po zbadaniu i rozpoczęciu problemów.

Możesz wykluczyć projekt, wykonując następujące podejścia:

- Tymczasowe usunięcie z aktywnej konfiguracji rozwiązania.

- Tworzenie konfiguracji rozwiązania, która nie zawiera projektu.

Aby uzyskać więcej informacji, zobacz [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Aby tymczasowo usunąć projekt z aktywnej konfiguracji rozwiązania

1. Na pasku menu wybierz kolejno opcje **Kompiluj** > **Configuration Manager**.

2. W tabeli **kontekstowe projektu** Znajdź projekt, który ma zostać wykluczony z kompilacji.

3. W kolumnie **kompilacja** dla projektu wyczyść pole wyboru.

4. Wybierz przycisk **Zamknij** , a następnie Skompiluj ponownie rozwiązanie.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Aby utworzyć konfigurację rozwiązania, która wyklucza projekt

1. Na pasku menu wybierz kolejno opcje **Kompiluj** > **Configuration Manager**.

2. Na liście **Konfiguracja aktywnego rozwiązania** wybierz pozycję  **\<nowe >** .

3. W polu **Nazwa** wprowadź nazwę konfiguracji rozwiązania.

4. Z listy **Kopiuj ustawienia z** wybierz konfigurację rozwiązania, dla której chcesz utworzyć nową konfigurację (na przykład **debugowanie**), a następnie wybierz przycisk **OK** .

5. W oknie dialogowym **Configuration Manager** wyczyść pole wyboru w kolumnie **kompilacja** dla projektu, który ma zostać wykluczony, a następnie wybierz przycisk **Zamknij** .

6. Na pasku narzędzi **Standardowy** Sprawdź, czy nowa konfiguracja rozwiązania jest aktywna konfiguracja w polu **konfiguracje rozwiązania** .

7. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

## <a name="see-also"></a>Zobacz także

- [O konfiguracjach kompilacji](../ide/understanding-build-configurations.md)
- [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Instrukcje: Kompiluj jednocześnie wiele konfiguracji](../ide/how-to-build-multiple-configurations-simultaneously.md)