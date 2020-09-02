---
title: Projektant przepływu pracy — Odbierz projektanta działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55f49a32036fcfd5e9f75f3d8dd61499c4af0b2e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875725"
---
# <a name="receive-activity-designer"></a>Receive, projektant działań

Projektant działań **Odbierz** służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.Receive> działania. <xref:System.ServiceModel.Activities.Receive>Działanie to działanie, które odbiera komunikat, który może być typem wbudowanym, takim jak <xref:System.ServiceModel.Channels.Message> <xref:System.IO.Stream> lub <xref:System.Xml.Linq.XElement> , lub kontraktem danych zdefiniowanym przez aplikację, umową komunikatu lub klasą XML, która może być serializowana.

## <a name="the-receive-activity"></a>Działanie Odbierz

<xref:System.ServiceModel.Activities.Receive>Działanie może odbierać pojedynczy element lub wiele elementów w zależności od typu odebranej zawartości. <xref:System.ServiceModel.Activities.SendReply>Działanie może być powiązane z <xref:System.ServiceModel.Activities.Receive> działaniem, które odbiera komunikat w ramach wzorca wymiany komunikatów żądania/odpowiedzi w usłudze.

### <a name="using-the-receive-activity-designer"></a>Korzystanie z projektanta działań odbioru

Dostęp do projektanta działania **Odbierz** w kategorii **Obsługa wiadomości** w **przyborniku**. Projektanta działań **odbioru** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> odbiorem. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **odbioru** lub w polu **DisplayName** siatki właściwości.

Aby utworzyć <xref:System.ServiceModel.Activities.SendReply> działanie i powiązać je z wybranym <xref:System.ServiceModel.Activities.Receive> działaniem, kliknij prawym przyciskiem myszy pozycję **Odbierz** działanie, a następnie kliknij pozycję **Utwórz element SendReply** w menu kontekstowym, a projektant **SendReplyToReceive** pojawia się poniżej projektanta **odbierania** . <xref:System.ServiceModel.Activities.SendReply>Działanie to działanie, które wysyła komunikat odpowiedzi w ramach wzorca wymiany komunikatów żądania/odpowiedzi w usłudze. Można go skonfigurować za pomocą narzędzia **SendReplyToReceive** Designer.

Alternatywnie można użyć projektanta szablonów **ReceiveAndSendReply** w kategorii **Obsługa wiadomości** w **przyborniku** , aby utworzyć parę wstępnie skonfigurowanych <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań. Aby uzyskać więcej informacji na temat używania szablonu **ReceiveAndSendReply** i **SendReplyToReceive** , zobacz temat [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) .

### <a name="the-receive-activity-properties"></a>Właściwości działania Odbierz

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.Receive> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości lub na Projektant przepływu pracy powierzchni. Jedyną wymaganą właściwością jest <xref:System.ServiceModel.Activities.Receive.OperationName%2A> Właściwość.

| Nazwa właściwości | Wymagany | Użycie |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Fałsz | Określa przyjazną nazwę <xref:System.ServiceModel.Activities.Receive> działania. Wartość domyślna to Receive.<br /><br /> Chociaż użycie wartości innej niż domyślna dla elementu friendly <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie takiej wartości. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Prawda | Określa nazwę operacji usługi zaimplementowanej przez to <xref:System.ServiceModel.Activities.Receive> działanie. Ta właściwość służy do konstruowania wartości domyślnej właściwości **Akcja** , jeśli właściwość **Akcja** nie jest jawnie ustawiona. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | Fałsz | Określa nazwę kontraktu usługi. Ta właściwość służy do grupowania operacji usługi w ramach poszczególnych umów dotyczących usług. Wszystkie <xref:System.ServiceModel.Activities.Receive> działania, które są takie same, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> są pogrupowane w ten sam kontrakt usługi (typ portu WSDL). Wartość domyślna to w pełni kwalifikowana nazwa środowiska CLR działania najwyższego poziomu (głównego). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | Fałsz | Określa komunikat lub zawartość parametru do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, wybierając przycisk wielokropka obok pola **zawartość** w siatce właściwości lub klikając przycisk **Definiuj...** obok etykiety **zawartość** na powierzchni projektanta działań **.** Wyświetla okno dialogowe **definicji zawartości** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [okno dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | Fałsz | Określa korelacje między <xref:System.ServiceModel.Activities.Receive> działaniami w ramach operacji usługi przepływu pracy z <xref:System.ServiceModel.MessageQuerySet> obiektem. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości w siatce właściwości, aby otworzyć okno dialogowe **Definicja CorrelatesOn** . Aby uzyskać więcej informacji na temat korzystania z tego okna dialogowego, zobacz temat okno [dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | Fałsz | Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do kierowania komunikat do odpowiedniego wystąpienia przepływu pracy.<br /><br /> Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> właściwości w siatce właściwości, aby otworzyć okno dialogowe **Edytor wyrażeń** . Więcej informacji o użyciu tego okna dialogowego można znaleźć w temacie How to [: Use the Expression Editor](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | Fałsz | Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które inicjują wiele <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które konfigurują to <xref:System.ServiceModel.Activities.Receive> działanie w ramach przepływu pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [okno dialogowe Dodawanie CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | Fałsz | Określa wartość określającą, czy nowe wystąpienie przepływu pracy jest tworzone w celu przetworzenia komunikatu, jeśli komunikat nie jest skorelowany z istniejącym wystąpieniem przepływu pracy. Jeśli wartość jest równa **true**, zostanie utworzone nowe wystąpienie przepływu pracy w celu przetworzenia komunikatu, gdy komunikat nie jest skorelowany z istniejącym wystąpieniem przepływu pracy. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | Fałsz | Określa kolekcję znanych typów dla operacji usługi zaimplementowanej przez to <xref:System.ServiceModel.Activities.Receive> działanie. Ta właściwość powinna być używana w połączeniu z <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwością ustawioną na <xref:System.Runtime.Serialization.DataContractSerializer> . Jest on ignorowany, jeśli <xref:System.Xml.Serialization.XmlSerializer> jest używany.<br /><br /> Wybierz przycisk wielokropka obok pola **KnownTypes** w siatce właściwości, aby wyświetlić okno dialogowe **Edytor kolekcji typów** , w którym można dodać odpowiednie typy. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | Fałsz | Określa <xref:System.Net.Security.ProtectionLevel> dla wiadomości.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> oznacza tylko uwierzytelnianie.<br />2.  <xref:System.Net.Security.ProtectionLevel> oznacza, że dane podpisywania mają zapewnić integralność przesyłanych danych.<br />3.  <xref:System.Net.Security.ProtectionLevel> oznacza szyfrowanie i podpisywanie danych w celu zapewnienia poufności i integralności przesyłanych danych. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | Fałsz | Określa typ serializatora, który ma być używany dla operacji usługi zaimplementowanej przez <xref:System.ServiceModel.Activities.Receive> działanie. Wartość domyślna to <xref:System.Runtime.Serialization.DataContractSerializer> , która serializować i deserializacji wystąpienia typu do strumienia XML lub dokumentu, który używa dostarczonego kontraktu danych. <xref:System.Xml.Serialization.XmlSerializer>Można również użyć, jeśli w kodzie XML jest wymagana większa kontrola. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | Fałsz | Określa nagłówek akcji wiadomości. Jeśli nie jest on jawnie ustawiony, jego wartość domyślna to: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>Zobacz też

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wysyłanie](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
