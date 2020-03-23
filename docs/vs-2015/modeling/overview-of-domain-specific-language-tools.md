---
title: Omówienie narzędzi językowych specyficznych dla domeny | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d38aed17d7fdaa694c8c5753705b28b0390dedfc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "72652143"
---
# <a name="overview-of-domain-specific-language-tools"></a>Przegląd narzędzi językowych właściwych dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia językowe specyficzne dla domeny (DSL [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Tools), które są hostowane w programie , umożliwiają projektowanie języka specyficznego dla domeny, a następnie generowanie wszystkiego, co użytkownicy muszą mieć do tworzenia modeli opartych na języku.

 Następujące narzędzia są zawarte w narzędzia dsl:

- Kreator projektu, który używa różnych szablonów rozwiązań, aby ułatwić rozpoczęcie tworzenia języka specyficznego dla domeny.

- Projektant graficzny do tworzenia i edytowania definicji języka specyficznej dla domeny.

- Aparat sprawdzania poprawności, który upewnia się, że definicja języka specyficzne dla domeny jest poprawnie sformułowany i wyświetla błędy i ostrzeżenia, jeśli występują problemy.

- Generator kodu, który przyjmuje definicję języka specyficznego dla domeny jako dane wejściowe i tworzy kod źródłowy jako dane wyjściowe.

## <a name="the-dsl-tools-solution"></a>Rozwiązanie dsl tools
 Kreator projektanta specyficznego dla domeny udostępnia następujące szablony rozwiązań:

- Przepływ zadań

- Diagramy klas

- Minimalny język

- Modele komponentów

- Minimalny WPF

- Minimalny windows.forms

- Biblioteka DSL

  Aby uzyskać więcej informacji, zobacz [Wybieranie szablonu rozwiązania językowego specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Kreator tworzy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie, które ma następujące projekty:

- Dsl

   Projekt Dsl definiuje język specyficzny dla domeny oraz jego narzędzia do edycji i przetwarzania.

- **Dslpackage**

   Projekt DslPackage określa sposób integracji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]narzędzi językowych z programem .

## <a name="the-dsl-tools-graphical-interface"></a>Interfejs graficzny DSL Tools
 Za pomocą interfejsu graficznego DSL Tools można dodawać elementy i relacje do języka specyficznego dla domeny. Po dodaniu elementów można zdefiniować ich wygląd, mapując je na kształty, dostosowując kolory i dodając dekoratory. Można również dodać elementy do przybornika.

## <a name="validation-in-dsl-tools"></a>Sprawdzanie poprawności w narzędziach DSL
 Dsl zapewnia jeden poziom sprawdzania poprawności, aby upewnić się, że model domeny spełnia podstawowe wymagania dotyczące generowania kodu. Zazwyczaj podczas tworzenia własnego języka specyficznego dla domeny, należy dodać własne sprawdzanie poprawności, aby wyrazić reguły logiki biznesowej. Aby uzyskać więcej informacji na temat sprawdzania poprawności [niestandardowej,](../modeling/validation-in-a-domain-specific-language.md)zobacz Sprawdzanie poprawności w języku specyficznym dla domeny .

 Zaleca się, aby podczas projektowania można często sprawdzać poprawność języka specyficznego dla domeny. Jeśli język specyficzny dla domeny ma błędy sprawdzania poprawności, nie można wygenerować kodu źródłowego. Proces generowania kodu źródłowego z szablonów jest wykonywany przez kliknięcie **przycisku Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań. Za każdym razem, gdy modyfikujesz definicję języka, upewnij się również, **że należy przekształć wszystkie szablony**. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie rozwiązania językowego specyficznego dla domeny](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Dostosowywanie narzędzi DSL
 Można podać dodatkowy kod, aby uściślić zachowanie modelu i zdefiniować ograniczenia dotyczące języka. W razie potrzeby można wprowadzić istotne zmiany, modyfikując szablony tekstu.

## <a name="distributing-your-dsl-solution"></a>Dystrybucja rozwiązania DSL
 DSL Tools generuje pakiet, który [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]jest hostowany w . Pakiet wyświetla przybornik, Eksplorator DSL i inne elementy interfejsu użytkownika, które umożliwiają użytkownikom tworzenie modeli przy użyciu języka specyficznego dla domeny.

 Podczas tworzenia i uruchamiania rozwiązania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]DSL Tools [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w drugim wystąpieniu pokazuje, jak język specyficzny dla domeny wygląda dla użytkownika języka. Po sprawdzeniu, czy wszystko działa `.vsix` poprawnie, można rozpowszechniać plik, który można znaleźć w folderze kompilacji projektu DslPackage. Ten plik może służyć do zainstalowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DSL jako rozszerzenia na innych komputerach.  Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązań językowych specyficznych dla domeny](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Zobacz też
 Słownik [narzędzi językowych specyficznych dla domeny wystąpienia](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) [eksperymentalnego](../extensibility/the-experimental-instance.md)
