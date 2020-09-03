---
title: 'Instrukcje: Rozwiązywanie problemów z szablonami | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c481b2b9c90b15f4cbc709cad89e5b772ad95cee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477082"
---
# <a name="how-to-troubleshoot-templates"></a>Porady: rozwiązywanie problemów z szablonami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli szablon nie zostanie załadowany w środowisku deweloperskim, istnieje kilka sposobów zlokalizowania problemu.

## <a name="validating-the-vstemplate-file"></a>Weryfikowanie pliku. vstemplate
 Jeśli plik. vstemplate w szablonie nie jest zgodny ze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] schematem szablonu, szablon może nie pojawić się w oknie dialogowym **Nowy projekt** .

#### <a name="to-validate-the-vstemplate-file"></a>Aby sprawdzić poprawność pliku. vstemplate

1. Znajdź plik zip, który zawiera szablon.

2. Wyodrębnij plik zip.

3. W menu **plik** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , kliknij polecenie **Otwórz**, a następnie kliknij **plik**.

4. Wybierz plik vstemplate szablonu, a następnie kliknij przycisk **Otwórz**.

5. Sprawdź, czy plik XML pliku. vstemplate jest zgodny ze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] schematem szablonu. Aby uzyskać więcej informacji na temat schematu. vstemplate, zobacz [Dokumentacja schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Aby uzyskać pomoc techniczną IntelliSense podczas tworzenia pliku. vstemplate, Dodaj `xmlns` atrybut do `VSTemplate` elementu i przypisz mu wartość `http://schemas.microsoft.com/developer/vstemplate/2005` .

6. Zapisz i zamknij plik. vstemplate.

7. Wybierz pliki dołączone do szablonu, kliknij prawym przyciskiem myszy, wybierz polecenie **Wyślij do**, a następnie kliknij **folder skompresowany (zip)**. Wybrane pliki są kompresowane do pliku zip.

8. Umieść nowy plik zip w tym samym katalogu, w którym znajduje się stary plik. zip.

9. Usuń wyodrębnione pliki szablonów i stary plik Template. zip.

## <a name="monitoring-the-event-log"></a>Monitorowanie dziennika zdarzeń
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rejestruje błędy podczas przetwarzania plików Template. zip. Jeśli szablon nie jest wyświetlany w oknie dialogowym **Nowy projekt** w oczekiwany sposób, można użyć **Podgląd zdarzeń** , aby rozwiązać problem.

#### <a name="to-locate-template-errors-in-event-viewer"></a>Aby zlokalizować błędy szablonów w Podgląd zdarzeń

1. W systemie Windows kliknij przycisk **Start**, kliknij przycisk **Panel sterowania**, kliknij dwukrotnie przycisk **Narzędzia administracyjne**, a następnie kliknij dwukrotnie przycisk **Podgląd zdarzeń**.

2. W lewym okienku kliknij pozycję **aplikacja**.

3. Wyszukaj zdarzenia z wartością **źródłową** `Visual Studio - VsTemplate` .

4. Kliknij dwukrotnie zdarzenie szablonu, aby wyświetlić błąd.

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md) [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md) [szablon programu Visual Studio — odwołanie do schematu](../extensibility/visual-studio-template-schema-reference.md)
