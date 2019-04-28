---
title: Opisywanie przepływu sterowania, przy użyciu fragmentów w diagramach sekwencji UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c296be2e3a00efcdf48bdd6e4442e88fc32b3695
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422539"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Opisywanie przepływu sterowania przy użyciu fragmentów w diagramach sekwencji UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie sekwencji UML *połączone fragmenty* pozwalają wyświetlić pętli, gałęzi i inne alternatywy.  
  
 Połączony fragment składa się z co najmniej jeden *operandy interakcji*, a każdy z nich zawiera co najmniej jeden wiadomości, zastosowania interakcji lub połączonego fragmentu.  
  
> [!NOTE]
> Ten temat dotyczy fragmentów w diagramach sekwencji. Aby uzyskać więcej informacji o tym, jak odczytać diagramy sekwencji UML, zobacz [UML Sequence Diagrams: Odwołanie](../modeling/uml-sequence-diagrams-reference.md). Aby uzyskać więcej informacji na temat narysować diagramy sekwencji UML, zobacz [UML Sequence Diagrams: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 ![Połączone fragmentu przyjmuje dwa argumenty operacji interakcji](../modeling/media/uml-seqfragments.png "UML_SeqFragments")  
  
 Dostępne są następujące elementy pokazano na rysunku.  
  
1. Połączony fragment. Istnieje kilka rodzajów połączonego fragmentu. W tym przykładzie jest Alt połączony fragment, którego można użyć, aby pokazać, że alternatywnych sekwencji komunikatów może wystąpić.  
  
2. Operandy interakcji. Każdy połączony fragment zawiera co najmniej jeden argument interakcji, który może zawierać wiadomości, zastosowania interakcji i mniejsze połączonego fragmentu. W tym przykładzie połączone Alt fragment ma dwie operacje interakcji, przedstawiający dwa alternatywnych sekwencji komunikatów.  
  
3. Każdy argument interakcji można wybrać, klikając pozycję wewnątrz niego oddzielnie. W tym przykładzie argument najważniejsze interakcji jest zaznaczone, tak, aby jego granicę są widoczne. Zwykle tylko jednoznaczny interakcji z operandów jest widoczna.  
  
    > [!NOTE]
    > Aby wybrać operand najważniejsze interakcji, możesz nie powinien klikać za blisko początku połączonego fragmentu.  
  
4. Osłony. Każdy argument interakcji można nadać ochrony. Opisuje warunku w ramach której zostanie wykonane komunikaty wewnątrz operand interakcji.  
  
## <a name="creating-combined-fragments"></a>Tworzenie połączone fragmentów  
 Aby uzyskać listę rodzajów fragment, można utworzyć, zobacz [rodzajów połączone fragmentu](#KindsOfFragment).  
  
#### <a name="to-create-a-combined-fragment"></a>Aby utworzyć połączony fragment  
  
1. Wybierz jeden komunikat lub sekwencję wiadomości, wszystkie rozpoczyna się w tej samej linii życia lub wykonywania wystąpienia.  
  
   > [!NOTE]
   > Jeśli wybierzesz więcej niż jeden komunikat, tworzą one muszą nieprzerwanie sekwencji.  
  
2. Kliknij prawym przyciskiem myszy jeden z komunikatów, wskaż opcję **Otocz**, a następnie kliknij typ połączonego fragmentu, który ma, takich jak **fragmentu połączone Alt**.  
  
    Pojawi się nowy połączony fragment. Nagłówek wskazuje typ połączonego fragmentu wybrano, takich jak **Alt**.  
  
    Wewnątrz połączonego fragmentu jest fragmentu, który zawiera komunikaty, które zostały wybrane.  
  
   Możesz dodać więcej operandów interakcji do niektórych rodzajów połączonego fragmentu.  
  
   Po zmianie rozmieszczenia wiadomości w połączony fragment, wybierz **Zmień rozmieszczanie układu** w menu skrótów, aby zmienić rozmiar ramki połączonego fragmentu.  
  
#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>Aby dodać nowe operand interakcji do połączonego fragmentu  
  
1. Kliknij prawym przyciskiem myszy spację wewnątrz interakcji argument operacji [2], poza wszelkie zawarte fragmentu i poniżej nagłówka połączonego fragmentu.  
  
2. Wskaż **Dodaj**.  
  
3. Kliknij przycisk **argumentu interakcji przed**, lub **Operand interakcji po**.  
  
4. Można dodawać komunikaty wewnątrz nowych operand interakcji za pomocą narzędzi wiadomości lub przez kopiowanie i wklejanie istniejące wiadomości.  
  
   Możesz ustawić **Guard** właściwość operandu interakcji do opisania warunków, w których są wykonywane komunikaty wewnątrz niego. Na przykład w **pętli** połączone fragmentu, osłony można użyć do określenia warunków, w którym nadal pętli. W **Alt** połączone fragmentu, można określić oddzielne warunek każdy argument interakcji.  
  
#### <a name="to-set-the-guard-of-an-interaction-operand"></a>Aby ustawić osłony operand interakcji  
  
1. Kliknij spację wewnątrz operand interakcji (2), poza wszelkie zawarte fragmentu.  
  
    Obramowanie wyboru pojawia się wokół operand interakcji i wokół warunek zabezpieczenia.  
  
    W pozycji w **właściwości** Pokazuje okno **Operand interakcji**.  
  
2. Typ warunku zabezpieczenia.  
  
    Warunek pojawi się w górnej części fragmentu (4).  
  
   Można ustawić właściwości niektóre rodzaje połączonego fragmentu.  
  
#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>Aby ustawić lub wyświetlić właściwości połączony fragment  
  
- Kliknij prawym przyciskiem myszy w tytule połączonego fragmentu, a następnie kliknij przycisk **właściwości**.  
  
    > [!NOTE]
    > Różne rodzaje połączonego fragmentu mają różne właściwości.  
  
## <a name="KindsOfFragment"></a> Rodzaje połączony Fragment  
  
### <a name="fragments-describing-control-flow"></a>Fragmenty opisywanie przepływu sterowania  
 Od prostego diagramu sekwencji pokazuje tylko jednej typowej sekwencji. Do opisania zmian, które mogą wystąpić w różnych przypadkach, można użyć następujących typów połączonego fragmentu.  
  
|Typ fragmentu|Opis|  
|-------------------|-----------------|  
|**zoptymalizowany pod kątem**|Opcjonalna. Otacza sekwencji, którzy mogą lub nie może mieć miejsce. Można określić, w guard, warunek, pod którym występuje.|  
|**ALT**|Zawiera listę fragmentów, zawierające alternatywnych sekwencji wiadomości. Tylko jednej sekwencji występuje przy każdej okazji.<br /><br /> Strażnik można umieścić w każdego fragmentu, aby wskazać, pod warunkiem, jakie można uruchomić. Ochrona programu **else** wskazuje fragmentu, który należy uruchomić, jeśli nie innych guard ma wartość true. Chroni wszystkie mają wartość false, jeśli ma nie **else**, a następnie wykonuje Brak fragmenty.|  
|**Loop**|Fragment powtarza pewną liczbę razy. Można wskazać w osłony warunek, pod którym należy powtórzyć.<br /><br /> Pętla połączone fragmenty mają właściwości podane **Min** i **Max**, które wskazują minimalną i maksymalną liczbę razy, które można powtarzać tego fragmentu. Wartość domyślna to Brak ograniczeń.|  
|**BREAK**|Jeśli ten fragment jest wykonywane, zostanie porzucony pozostałej części sekwencji. Osłony służy do wskazania stanu, w którym nastąpi przerwanie.|  
|**Par**|Równoległe. Mogą się przeplatać zdarzenia we fragmentach.|  
|**Krytyczne**|Używane w obrębie fragmentu Par lub Seq. Wskazuje, czy wiadomości, w tym fragmencie nie muszą się przeplatać z inne komunikaty.|  
|**SEQ**|Istnieją dwa lub więcej fragmentów operand. Komunikaty dotyczące tej samej linii życia, musi nastąpić zgodnie z kolejnością fragmenty. W przypadku, gdy nie obejmują tej samej linii życia, wiadomości z różnych fragmentów może być przemieszane równolegle.|  
|**Strict**|Istnieją dwa lub więcej fragmentów operand. Fragmenty musi przypadać w podanej kolejności.|  
  
### <a name="fragments-about-how-to-interpret-the-sequence"></a>Fragmenty o tym, jak interpretować sekwencji  
 Domyślnie diagram sekwencji stanów szereg wiadomości, które mogą wystąpić. W działającym systemie inne komunikaty może się zdarzyć, że nie zostały wybrane do wyświetlenia na diagramie.  
  
 Następujące typy fragment może służyć do zmiany tej interpretacji.  
  
|Typ fragmentu|Opis|  
|-------------------|-----------------|  
|**Należy wziąć pod uwagę**|Określa listę komunikatów, które opisano w tym fragmencie. Inne komunikaty mogą występować w działającym systemie, ale nie są istotne dla celów tego opisu.<br /><br /> Typ listy w **wiadomości** właściwości.|  
|**Ignoruj**|Lista komunikatów, które nie są opisane w tym fragmencie. One może wystąpić w działającym systemie, ale nie są istotne dla celów tego opisu.<br /><br /> Typ listy w **wiadomości** właściwości.|  
|**Assert**|Fragment argument określa jedyną prawidłową sekwencji. Zazwyczaj używane w obrębie fragmentu rozważ lub Ignoruj.|  
|**minus**|Sekwencja przedstawione w tym fragmencie nie musi realizowane. Zazwyczaj używane w obrębie fragmentu rozważ lub Ignoruj.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagramy sekwencji UML: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)   
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)
