---
title: Standardowe stereotypy dla modeli UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, stereotypes
- UML diagrams, stereotypes
ms.assetid: 8a8c2321-1cae-4ba8-bb9e-23495c3404d8
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ebf931773577add65a7479c7dcd90da9c58c556
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770702"
---
# <a name="standard-stereotypes-for-uml-models"></a>Standardowe stereotypy dla modeli UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za dodawanie stereotypów do elementów modelu UML, aby podać dodatkowe informacje dla czytnika lub do przetworzenia maszyny. Stereotypy są zdefiniowane w profilach, a każdy profil zawiera zbiór stereotypów. Kilka profilów są dostarczane z programem Visual Studio. Można także zdefiniować własne profile, które mogą zawierać własne stereotypów. Aby uzyskać więcej informacji, zobacz [Definiowanie profilu w celu rozszerzenia UML](../modeling/define-a-profile-to-extend-uml.md).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="the-standard-profiles"></a>Standardowa profilów  
 Następujące profile są dostępne w obsługiwanej wersji programu Visual Studio, zaraz po jego zainstalowaniu.  
  
|Profil|Cel|  
|-------------|-------------|  
|[Profil standardowy UML pamięci podręcznej L2](#L2)|Standardowy zestaw stereotypów, które mogą służyć do dodawania dodatkowych informacji na temat elementu lub relacji.|  
|[L3 standardowy profil UML](#L3)|Standardowy zestaw stereotypów, które mogą służyć do dodawania dodatkowych informacji na temat elementu lub relacji.|  
|[C# Profile](#NetProfile)|Jeśli planujesz klasę lub inny element w modelu UML do reprezentowania kodu programu, możesz to zasygnalizować, stosując jednemu ze stereotypów z profilu C#.<br /><br /> Tych stereotypów również dodać właściwości do elementów modelu.|  
  
 Podczas tworzenia nowego modelu UML standardowa L2 profilów UML i L3 są połączone z modelu, chyba że usuniesz łącza.  
  
 Aby użyć stereotypy w dowolnym z tych profilów, najpierw trzeba połączyć profil do pakietu lub modelu, który zawiera elementy, aby stosować je do.  
  
#### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Aby połączyć profil modelu lub pakietu  
  
1.  Otwórz **Eksploratora modelu UML**. Na **architektury** menu wskaż **Windows**, a następnie kliknij przycisk **Eksploratora modelu UML**.  
  
2.  Zlokalizuj pakiet lub model, który zawiera wszystkie elementy, których można również zastosować stereotypy w profilu.  
  
3.  Kliknij prawym przyciskiem myszy pakiet lub model, a następnie kliknij przycisk **właściwości**.  
  
4.  W **właściwości** oknie **profile** właściwości profilów, które chcesz.  
  
#### <a name="to-remove-the-link-between-a-profile-and-a-model-or-package"></a>Aby usunąć powiązanie profilu i modelu lub pakietu  
  
1.  W Eksploratorze modelu UML, kliknij prawym przyciskiem myszy modelu lub pakietu, a następnie kliknij przycisk **właściwości**.  
  
2.  W oknie właściwości ustaw **profile** właściwość pustą.  
  
    > [!NOTE]
    >  Można odłączyć elementy od profilu, tylko wtedy, gdy żaden z elementów w modelu lub pakietu Użyj Stereotypy tego profilu.  
  
#### <a name="to-apply-a-stereotype-to-a-model-element"></a>Aby zastosować stereotyp do elementu modelu  
  
1.  Kliknij prawym przyciskiem myszy element modelu w diagramie lub w **Eksploratora modelu UML**, a następnie kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Stereotypy** właściwości i wybierz pozycję stereotypów, który chcesz zastosować.  
  
     Wybrane Stereotypy pojawiają się ostrokątnego «» w element modelu, w przypadku większości elementu.  
  
    > [!NOTE]
    >  Jeśli nie widzisz **Stereotypy** właściwości, lub jeśli nie ma stereotyp ma, upewnij się, że element modelu znajduje się wewnątrz pakietu lub modelu, do którego został połączony odpowiedni profil.  
  
3.  Niektóre Stereotypy umożliwiają ustawienie wartości dodatkowe właściwości dla elementu modelu. Aby wyświetlić te właściwości, rozwiń węzeł **Stereotypy** właściwości.  
  
###  <a name="L2"></a> Profil standardowy UML pamięci podręcznej L2  
 Stereotypy następujące może służyć do specialize znaczenie elementów modelu UML, chyba, że link do profilu została usunięta z modelu.  
  
 Dokładne znaczenie tych stereotypów jest określana przez własnych Konwencji lokalnych i narzędzi, które można użyć do przetwarzania modelu.  
  
|Stereotyp|Informacje zawarte w tym artykule dotyczą|Znaczenie|  
|----------------|----------------|-------------|  
|pomocnicze|Class|Klasa, która obsługuje innej klasy, zazwyczaj przez zaimplementowanie dodatkowej logiki. Inne klasy mogą mieć stereotyp «fokus».|  
| — wywołanie|Zależność|Klasa klienta wywołania operacji dostawcy.|  
|tworzenie|Zależność|Klasa klienta tworzy wystąpienia dostawcy.|  
|tworzenie|Komunikat|Nadawca tworzenia odbiornika.|  
|tworzenie|Operacja|Ta operacja jest konstruktora.|  
|pochodzi|Zależność|Element klienta jest obliczany całkowicie lub częściowo od dostawcy.|  
|destroy|Operacja|Operacja niszczy jego wystąpienia.|  
|dokument|Artefakt|Element "pliku" nie jest źródłem lub pliku wykonywalnego.|  
|jednostka|Składnik|Składnik reprezentuje koncepcji biznesowych.|  
|pliku wykonywalnego|Artefakt|Plik wykonywalny "pliku".|  
|plik|Artefakt|Pliku fizycznego.|  
|fokus|Class|Klasą zdefiniowanie logiki biznesowej core, obsługiwane przez kilka klas "pomocnicze".|  
|szablon|Package|Ten pakiet definiuje wzorzec projektowania do wielokrotnego użytku.|  
|Implementowanie|Składnik|Implementacja specyfikacji «».|  
|implementationClass|Class|Klasa Opisuje implementację i każde wystąpienie środowiska uruchomieniowego ma jedną klasę stały implementacji. Natomiast określenie "typu".|  
|Utwórz wystąpienie|Zależność|Klient tworzy wystąpienia dostawcy.|  
|biblioteka|Artefakt|Biblioteka "pliku".|  
|metaclass|Class|Wystąpienia tej klasy są również klasami.|  
|modelLibrary|Package|Zawiera elementy modelu, które ma być ponownie używane przez zaimportowanie pakietów. Zazwyczaj zdefiniowane jako część profilu i automatycznie importowane przez aplikację profilu.|  
|proces|Składnik|Składnik usługi opartej na transakcjach, lub takiego, który prowadzi wątku.|  
|Realizacja|Klasy, interfejsu, składnik|W tym artykule opisano implementację.|  
|Aktualizuj|Zależność|Klasa klienta, składnika lub pakiet zawiera więcej informacji na temat specyfikacji lub projektu od dostawcy.|  
|Odpowiedzialność|Zależność|Komentarz na końcu dostawcy zależność definiuje obowiązki klienta klasy lub składnika.|  
|skrypt|Artefakt|Interpretowanej "plik".|  
|Wyślij|Zależność|Źródło działania wysyła sygnał docelowy.|  
|usługa|Składnik|Składnik bezstanowe.|  
|source|Artefakt|Nadawać "plik".|  
|specyfikacja|Klasy, interfejsu, składnik|Określa zachowanie składnika lub obiektu bez zdefiniowania, jak działa wewnętrznie.|  
|Podsystem|Składnik|Część dużym systemie. Podsystem na diagramie przypadków użycia jest składnikiem za pomocą stereotyp podsystemu.|  
|śledzenie|Zależność|Element klienta jest częścią projektu, która realizuje dostawcy. Po obu stronach tę zależność zwykle znajdują się w różnych modelach. Jedną z tych modeli jest realizacja innych.|  
|— typ|Class|Określa zachowanie obiektu bez podania, jak jest zaimplementowana. Obiekt jest elementem członkowskim typu, jeśli są zgodne ze specyfikacją.|  
|utility|Class|Kolekcja funkcji statycznych. Klasa nie ma żadnych wystąpień.|  
  
###  <a name="L3"></a> L3 standardowy profil UML  
 Stereotypy następujące może służyć do specialize znaczenie elementów modelu UML, jeśli profil nie zostało odłączone od modelu.  
  
 Dokładne znaczenie tych stereotypów jest określana przez własnych Konwencji lokalnych i narzędzi, które można użyć do przetwarzania modelu.  
  
|Stereotyp|Informacje zawarte w tym artykule dotyczą|Opis|  
|----------------|----------------|-----------------|  
|buildComponent|Składnik|Kolekcja elementów używanych do definiowania kompilacji.|  
|metaModel|Model|Określa język modelowania, takich jak wariant UML lub języka specyficznego dla domeny.|  
|systemModel|Model|Model, który jest kolekcją modeli, które dotyczą tego samego systemu, na przykład specyfikację, realizacja i śledzenia relacji między nimi.|  
  
##  <a name="NetProfile"></a> C# Profile  
 Stereotypy zdefiniowane w tym profilu pozwalają wskazać, że element modelu ma na celu translacji na kod programu. Każdy stereotyp definiuje dodatkowe właściwości, które można ustawić dla elementu modelu.  
  
 Aby udostępnić te stereotypów, połączyć modelu lub pakietu profil C#. Mogą następnie zastosować Stereotypy do elementów modelu, w tym modelu lub pakietu.  
  
 Dostępne Stereotypy elementów, do których mają one zastosowanie i dodatkowe właściwości, które są dostępne są podsumowane w poniższej tabeli.  
  
|Stereotyp|Informacje zawarte w tym artykule dotyczą|Właściwości|  
|----------------|----------------|----------------|  
|**C# Class**|Klasa UML<br /><br /> Składnik|**Atrybuty CLR**<br /><br /> **Jest częściowy**<br /><br /> **Jest zapieczętowany**<br /><br /> **Jest statyczny**<br /><br /> **Jest niebezpieczny**<br /><br /> **Widoczność pakietu**|  
|**Struktura C#**|Klasa UML<br /><br /> Składnik|**Atrybuty CLR**<br /><br /> **Jest częściowy**<br /><br /> **Jest niebezpieczny**<br /><br /> **Widoczność pakietu**|  
|**C# globalnego elementów członkowskich**|Klasa UML<br /><br /> Składnik|**Atrybuty CLR**|  
|**Interfejs C#**|Interfejs UML|**Atrybuty CLR**<br /><br /> **Jest częściowy**<br /><br /> **Widoczność pakietu**|  
|**Wyliczenie C#**|Wyliczenie UML|**ClrAttributes**<br /><br /> **Typ podstawowy**|  
|**Przestrzeń nazw C#**|Pakiet UML|**Atrybuty CLR**<br /><br /> **Nazwa podstawowa**<br /><br /> **Używanie przestrzeni nazw**|  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie stereotypów do elementów modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Dostosowywanie modelu z profilami i stereotypami](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Definiowanie profilu w celu rozszerzenia kodu UML](../modeling/define-a-profile-to-extend-uml.md)
