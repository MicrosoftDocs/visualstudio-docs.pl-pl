---
title: 'Instrukcje: Wykluczanie projektów z kompilacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffa2b0fd8cab35fc73031d3ead8a5803558c2c07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667940"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Poradnik: Wykluczanie projektów z kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz skompilować rozwiązanie bez kompilowania wszystkich projektów, które zawiera. Na przykład można wykluczyć projekt, który przerywa kompilację. Następnie można skompilować projekt po zbadaniu i rozpoczęciu problemów.

 Możesz wykluczyć projekt, wykonując następujące podejścia:

- Tymczasowe usunięcie z aktywnej konfiguracji rozwiązania.

- Tworzenie konfiguracji rozwiązania, która nie zawiera projektu.

  Aby uzyskać więcej informacji, zobacz [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md).

### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Aby tymczasowo usunąć projekt z aktywnej konfiguracji rozwiązania

1. Na pasku menu wybierz **kompilacja**, **Configuration Manager**.

2. W tabeli **kontekstowe projektu** Znajdź projekt, który ma zostać wykluczony z kompilacji.

3. W kolumnie **kompilacja** dla projektu wyczyść pole wyboru.

4. Wybierz przycisk **Zamknij** , a następnie Skompiluj ponownie rozwiązanie.

### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Aby utworzyć konfigurację rozwiązania, która wyklucza projekt

1. Na pasku menu wybierz **kompilacja**, **Configuration Manager**.

2. Na liście **Konfiguracja aktywnego rozwiązania** wybierz opcję **\<New>** .

3. W polu **Nazwa** wprowadź nazwę konfiguracji rozwiązania.

4. Z listy **Kopiuj ustawienia z** wybierz konfigurację rozwiązania, dla której chcesz utworzyć nową konfigurację (na przykład **debugowanie**), a następnie wybierz przycisk **OK** .

5. W oknie dialogowym **Configuration Manager** wyczyść pole wyboru w kolumnie **kompilacja** dla projektu, który ma zostać wykluczony, a następnie wybierz przycisk **Zamknij** .

6. Na pasku narzędzi **Standardowy** Sprawdź, czy nowa konfiguracja rozwiązania jest aktywna konfiguracja w polu **konfiguracje rozwiązania** .

7. Na pasku menu wybierz **kompilacja**, **Skompiluj ponownie rozwiązanie**.

## <a name="see-also"></a>Zobacz też
 [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md) [instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md) [instrukcje: jednoczesne kompilowanie wielu konfiguracji](../ide/how-to-build-multiple-configurations-simultaneously.md)
