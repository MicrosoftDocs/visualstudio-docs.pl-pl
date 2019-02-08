---
title: 'Instrukcje: Wykluczanie projektów z kompilacji'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef85067ca3478bb2387f1f47a35938805f5fe0c5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924594"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Instrukcje: Wykluczanie projektów z kompilacji

Możesz tworzyć rozwiązania, bez konieczności tworzenia wszystkie projekty, które zawiera. Może na przykład wykluczyć projekt, który przerywa kompilację. Można następnie utworzyć projekt po badania i adres problemy.

Projekt może wyłączyć, korzystając z następujących metod:

-   Usunięcie go tymczasowo z aktywnej konfiguracji rozwiązania.

-   Tworzenie konfiguracji rozwiązania, które nie obejmują projektu.

Aby uzyskać więcej informacji, zobacz [konfiguracje kompilacji omówienie](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Aby tymczasowo usunięcie projektu z aktywnej konfiguracji rozwiązania

1.  Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**.

2.  W **projektu kontekstów** tabeli, Znajdź projekt, które chcesz wykluczyć z kompilacji.

3.  W **kompilacji** kolumny dla projektu, usuń zaznaczenie pola wyboru.

4.  Wybierz **Zamknij** przycisk, a następnie ponownie skompiluj rozwiązanie.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Umożliwia utworzenie konfiguracji rozwiązania, który wyklucza projektu

1.  Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**.

2.  W **Konfiguracja rozwiązania aktywnego** wybierz  **\<nowy >**.

3.  W **nazwa** wprowadź nazwę dla konfiguracji rozwiązania.

4.  W **Kopiuj ustawienia** wybierz konfiguracji rozwiązania, na którym chcesz utworzyć nową konfigurację (na przykład **debugowania**), a następnie wybierz **OK** przycisku .

5.  W **programu Configuration Manager** okno dialogowe, wyczyść pole wyboru w **kompilacji** kolumny dla projektu, który chcesz wykluczyć, a następnie wybierz **Zamknij** przycisku.

6.  Na **standardowa** narzędzi, sprawdź, czy nowa konfiguracja rozwiązania jest aktywna konfiguracja w **konfiguracje rozwiązania** pole.

7.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

## <a name="see-also"></a>Zobacz także

- [O konfiguracjach kompilacji](../ide/understanding-build-configurations.md)
- [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Instrukcje: Równoczesne kompilowanie wielu konfiguracji](../ide/how-to-build-multiple-configurations-simultaneously.md)