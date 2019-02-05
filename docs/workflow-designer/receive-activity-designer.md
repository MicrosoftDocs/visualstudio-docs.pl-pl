---
title: Projektant przepływu pracy — Receive, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c75b635cbdce7662c9e3a30237edb3e004ab7d0c
ms.sourcegitcommit: 0342f99120fbd603b8f06f7e9166c39f2896827a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742446"
---
# <a name="receive-activity-designer"></a>Receive, projektant działań

**Receive** projektanta działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.Receive> działania. A <xref:System.ServiceModel.Activities.Receive> działania to działanie, które odbiera komunikat, który może być wbudowany typ taką jak <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> lub <xref:System.Xml.Linq.XElement>, lub kontraktu danych zdefiniowanych przez aplikację, kontraktu komunikatu lub klasy XML, który może być serializowany.

## <a name="the-receive-activity"></a>Odbieranie działania

<xref:System.ServiceModel.Activities.Receive> Działania mogą otrzymać pojedynczy element lub wiele elementów, w zależności od typu odbierać zawartość użyta. A <xref:System.ServiceModel.Activities.SendReply> działanie może być powiązana z <xref:System.ServiceModel.Activities.Receive> działanie, które otrzymuje komunikat w ramach wymiany komunikatów żądań/odpowiedzi w usłudze.

### <a name="using-the-receive-activity-designer"></a>Za pomocą Receive, Projektant działań

Dostęp do **Receive** projektanta działań w **komunikatów** kategorii **przybornika**. **Receive** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczone. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> Receive. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **Receive** projektanta działań lub **DisplayName** pola siatki właściwości.

Do utworzenia <xref:System.ServiceModel.Activities.SendReply> działania i powiąż go do wybranych <xref:System.ServiceModel.Activities.Receive> działania, kliknij prawym przyciskiem myszy **Receive** działania projektanta, kliknij przycisk **tworzenie SendReply** element w menu kontekstowym i **SendReplyToReceive** pojawi się okno projektanta poniżej **Receive** projektanta. <xref:System.ServiceModel.Activities.SendReply> Działanie jest działanie powodujące wysłanie komunikatu odpowiedzi w ramach wymiany komunikatów żądań/odpowiedzi w usłudze. Może być konfigurowana przy użyciu **SendReplyToReceive** projektanta.

Alternatywnie **ReceiveAndSendReply** Projektant szablonów w **komunikatów** kategorii **przybornika** może służyć do tworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Receive>i <xref:System.ServiceModel.Activities.SendReply> działania. Aby uzyskać więcej informacji na temat użytkowania **ReceiveAndSendReply** i **SendReplyToReceive** szablonu, zobacz [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) tematu.

### <a name="the-receive-activity-properties"></a>Odbieranie właściwości działania

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.Receive> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta przepływów pracy. To jedyna wymagana właściwość <xref:System.ServiceModel.Activities.Receive.OperationName%2A> właściwości.


| Nazwa właściwości | Wymagane | Użycie |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Określa przyjazną nazwę <xref:System.ServiceModel.Activities.Receive> działania. Wartość domyślna to Receive.<br /><br /> Mimo że użycie wartości innych niż domyślne przyjazna <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem jest użycie tych wartości. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Prawda | Określa nazwę operacji usługi implementowany przez to <xref:System.ServiceModel.Activities.Receive> działania. Ta właściwość jest używana do konstruowania wartością domyślną dla **akcji** właściwość Jeśli **akcji** właściwość nie została jawnie ustawiona. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | Określa nazwę kontraktu usługi. Ta właściwość jest używana do grupy operacji usługi pojedynczej usługi umowy. Wszystkie <xref:System.ServiceModel.Activities.Receive> działań, które mają taki sam <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> są zgrupowane w tej samej umowy serwisowej (typ portu WSDL). Wartość domyślna to w pełni kwalifikowana nazwa CLR działania najwyższego poziomu (root). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytować tej właściwości, wybierając przycisk wielokropka obok **zawartości** w siatce właściwości lub klikając **Definiuj...**  przycisk obok **zawartości** etykiety na **Receive** powierzchni projektanta działań. Wyświetl oba **definicji zawartości** okna dialogowego. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | Określa korelacji między <xref:System.ServiceModel.Activities.Receive> działania w operacji usługi przepływu pracy przy użyciu <xref:System.ServiceModel.MessageQuerySet> obiektu. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości siatki właściwości, aby otworzyć **definice Vlastnosti Correlateson** okno dialogowe. Aby uzyskać więcej informacji na temat użycia tego okna dialogowego, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używana do rozsyłania wiadomości dla wystąpienia przepływu pracy odpowiednie.<br /><br /> Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> właściwości siatki właściwości, aby otworzyć **edytora wyrażeń** okno dialogowe. Aby uzyskać więcej informacji na temat użycia tego okna dialogowego, zobacz [jak: Używanie edytora wyrażeń](../workflow-designer/how-to-use-the-expression-editor.md) tematu. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | Określa kolekcję elementów <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **Dodaj inicjatory korelacji** okno dialogowe. Aby uzyskać więcej informacji o korzystaniu z tego pola, zobacz [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu. |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | Określa wartość, która określa, czy nowe wystąpienia przepływu pracy jest tworzony przetworzyć komunikatu, jeśli komunikat nie odnoszą się do istniejącego wystąpienia przepływu pracy. Jeśli wartość jest równa **true**, tworzone jest nowe wystąpienie przepływu pracy w przetworzyć komunikatu, gdy komunikat nie jest skorelowany z istniejącym wystąpieniem przepływu pracy. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | Określa kolekcję elementów znanych typów dla operacji usługowej implementowany przez to <xref:System.ServiceModel.Activities.Receive> działania. Ta właściwość powinna być używana w połączeniu z <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwością <xref:System.Runtime.Serialization.DataContractSerializer>. Jest ignorowana, jeśli <xref:System.Xml.Serialization.XmlSerializer> jest używany.<br /><br /> Wybierz przycisk wielokropka obok **element KnownTypes** w siatce właściwości do wyświetlenia **Editor typu Kolekce** okno dialogowe, za pomocą którego można dodawać odpowiednie typy. Aby uzyskać więcej informacji o korzystaniu z tego pola, zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) tematu. |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | Określa <xref:System.Net.Security.ProtectionLevel> dla wiadomości.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> oznacza, że tylko uwierzytelnianie.<br />2. <xref:System.Net.Security.ProtectionLevel> oznacza, że podpisywania danych do zapewnienia integralności przesyłanych danych.<br />3. <xref:System.Net.Security.ProtectionLevel> oznacza, że szyfrowania i podpisywania danych w celu zapewnienia poufności i integralności przesyłanych danych. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | Określa typ serializator do użycia dla operacji usługowej implementowany przez <xref:System.ServiceModel.Activities.Receive> działania. Wartość domyślna to <xref:System.Runtime.Serialization.DataContractSerializer>, który serializuje i deserializuje wystąpienia typu do strumień XML lub dokumentu, który używa kontraktu danych. <xref:System.Xml.Serialization.XmlSerializer> Można również, jeśli większą kontrolę jest wymagane w pliku XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | Określa nagłówek akcji w wiadomości. Jeśli nie jest jawnie ustawiona wartość ustawiona wartość domyślna: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Zobacz także

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
