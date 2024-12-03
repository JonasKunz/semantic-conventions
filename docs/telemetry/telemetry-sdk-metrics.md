<!--- Hugo front matter used to generate the website version of this page:
linkTitle: SDK Metrics
--->

# Semantic Conventions for OpenTelemetry SDK metrics

**Status**: [Experimental][DocumentStatus]

This document describes metrics emitted by the OpenTelemetry SDK components themselves about their internal state.

<!-- Re-generate TOC with `make markdown-toc` -->

<!-- toc -->

- [Span Metrics](#span-metrics)
  - [Metric: `telemetry.sdk.span.ended_count`](#metric-telemetrysdkspanended_count)
  - [Metric: `telemetry.sdk.span.sampled_count`](#metric-telemetrysdkspansampled_count)
  - [Metric: `telemetry.sdk.span.processor.queue_size`](#metric-telemetrysdkspanprocessorqueue_size)
  - [Metric: `telemetry.sdk.span.processor.queue_capacity`](#metric-telemetrysdkspanprocessorqueue_capacity)
  - [Metric: `telemetry.sdk.span.processor.spans_submitted`](#metric-telemetrysdkspanprocessorspans_submitted)
  - [Metric: `telemetry.sdk.span.processor.spans_processed`](#metric-telemetrysdkspanprocessorspans_processed)
  - [Metric: `telemetry.sdk.span.exporter.spans_submitted`](#metric-telemetrysdkspanexporterspans_submitted)
  - [Metric: `telemetry.sdk.span.exporter.spans_processed`](#metric-telemetrysdkspanexporterspans_processed)

<!-- tocstop -->

## Span Metrics

### Metric: `telemetry.sdk.span.ended_count`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.telemetry.sdk.span.ended_count -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `telemetry.sdk.span.ended_count` | Counter | `1` | The number of spans which have been ended | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `telemetry.sdk.span.sampled_count`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.telemetry.sdk.span.sampled_count -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `telemetry.sdk.span.sampled_count` | Counter | `1` | The number of spans which have been ended AND are sampled | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `telemetry.sdk.span.processor.queue_size`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.telemetry.sdk.span.processor.queue_size -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `telemetry.sdk.span.processor.queue_size` | UpDownCounter | `1` | The number of spans in the queue of a given instance of an SDK span processor [1] | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1]:** Only applies to span processors which use a queue, e.g. the SDK Batching Span Processor.

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`telemetry.sdk.component.id`](/docs/attributes-registry/telemetry.md) | string | A name uniquely identifying the instance of the OpenTelemetry SDK component within its containing SDK instance. [1] | `batch-span-0`; `custom-name` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| [`telemetry.sdk.processor.type`](/docs/attributes-registry/telemetry.md) | string | A name identifying the type of the OpenTelemetry SDK processor. | `batch-span`; `MyCustomProcessor` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1] `telemetry.sdk.component.id`:** The SDK MAY allow users to provide an id for the component instances. If no id is provided by the user,
the SDK SHOULD automatically assign an id. Because this attribute is used in metrics, the SDK MUST ensure a low cardinality in that case.
E.g. it MUST NOT use a UUID.
It instead MAY do that by using the following pattern as value: `<telemetry.sdk.processor/exporter.type>-<instance-counter>`:
Hereby, `<instance-counter>` is a monotonically increasing counter (starting with `0`), which is incremented every time an
instance of the given component type is created.
For example, the first Batch Span Processor will have `batch-span-0` as `telemetry.sdk.component.id`, the second one `batch-span-1` and so one.
These values will therefore be reused in the case of an application restart.

---

`telemetry.sdk.processor.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `batch-span` | The builtin SDK Batching Span Processor | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `simple-span` | The builtin SDK Simple Span Processor | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `telemetry.sdk.span.processor.queue_capacity`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.telemetry.sdk.span.processor.queue_capacity -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `telemetry.sdk.span.processor.queue_capacity` | Gauge | `1` | The maximum number of spans the queue of a given instance of an SDK span processor can hold [1] | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1]:** Only applies to span processors which use a queue, e.g. the SDK Batching Span Processor.

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`telemetry.sdk.component.id`](/docs/attributes-registry/telemetry.md) | string | A name uniquely identifying the instance of the OpenTelemetry SDK component within its containing SDK instance. [1] | `batch-span-0`; `custom-name` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| [`telemetry.sdk.processor.type`](/docs/attributes-registry/telemetry.md) | string | A name identifying the type of the OpenTelemetry SDK processor. | `batch-span`; `MyCustomProcessor` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1] `telemetry.sdk.component.id`:** The SDK MAY allow users to provide an id for the component instances. If no id is provided by the user,
the SDK SHOULD automatically assign an id. Because this attribute is used in metrics, the SDK MUST ensure a low cardinality in that case.
E.g. it MUST NOT use a UUID.
It instead MAY do that by using the following pattern as value: `<telemetry.sdk.processor/exporter.type>-<instance-counter>`:
Hereby, `<instance-counter>` is a monotonically increasing counter (starting with `0`), which is incremented every time an
instance of the given component type is created.
For example, the first Batch Span Processor will have `batch-span-0` as `telemetry.sdk.component.id`, the second one `batch-span-1` and so one.
These values will therefore be reused in the case of an application restart.

---

`telemetry.sdk.processor.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `batch-span` | The builtin SDK Batching Span Processor | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `simple-span` | The builtin SDK Simple Span Processor | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `telemetry.sdk.span.processor.spans_submitted`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.telemetry.sdk.span.processor.spans_submitted -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `telemetry.sdk.span.processor.spans_submitted` | Counter | `1` | The number of spans submitted for processing to this span processor. [1] | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1]:** A span is considered submitted when the first callback has been called which triggers processing of the span for the given processor.
For the Batching and Simple Span Processors this metric therefore MUST be incremented on invocations of the `on_end` span processor callback.

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`telemetry.sdk.component.id`](/docs/attributes-registry/telemetry.md) | string | A name uniquely identifying the instance of the OpenTelemetry SDK component within its containing SDK instance. [1] | `batch-span-0`; `custom-name` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| [`telemetry.sdk.processor.type`](/docs/attributes-registry/telemetry.md) | string | A name identifying the type of the OpenTelemetry SDK processor. | `batch-span`; `MyCustomProcessor` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1] `telemetry.sdk.component.id`:** The SDK MAY allow users to provide an id for the component instances. If no id is provided by the user,
the SDK SHOULD automatically assign an id. Because this attribute is used in metrics, the SDK MUST ensure a low cardinality in that case.
E.g. it MUST NOT use a UUID.
It instead MAY do that by using the following pattern as value: `<telemetry.sdk.processor/exporter.type>-<instance-counter>`:
Hereby, `<instance-counter>` is a monotonically increasing counter (starting with `0`), which is incremented every time an
instance of the given component type is created.
For example, the first Batch Span Processor will have `batch-span-0` as `telemetry.sdk.component.id`, the second one `batch-span-1` and so one.
These values will therefore be reused in the case of an application restart.

---

`telemetry.sdk.processor.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `batch-span` | The builtin SDK Batching Span Processor | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `simple-span` | The builtin SDK Simple Span Processor | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `telemetry.sdk.span.processor.spans_processed`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.telemetry.sdk.span.processor.spans_processed -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `telemetry.sdk.span.processor.spans_processed` | Counter | `1` | The number of spans for which the processing has finished, either successful or failed [1] | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1]:** For successful processing, `error.type` must be empty. For failed processing, `error.type` must contain the failure cause.

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`error.type`](/docs/attributes-registry/error.md) | string | A low-cardinality description of the failure reason. SDK Batching Span Processors MUST use `queue full` for spans dropped due to a full queue. [1] | `queue full` | `Recommended` | ![Stable](https://img.shields.io/badge/-stable-lightgreen) |
| [`telemetry.sdk.component.id`](/docs/attributes-registry/telemetry.md) | string | A name uniquely identifying the instance of the OpenTelemetry SDK component within its containing SDK instance. [2] | `batch-span-0`; `custom-name` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| [`telemetry.sdk.processor.type`](/docs/attributes-registry/telemetry.md) | string | A name identifying the type of the OpenTelemetry SDK processor. | `batch-span`; `MyCustomProcessor` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1] `error.type`:** The `error.type` SHOULD be predictable, and SHOULD have low cardinality.

When `error.type` is set to a type (e.g., an exception type), its
canonical class name identifying the type within the artifact SHOULD be used.

Instrumentations SHOULD document the list of errors they report.

The cardinality of `error.type` within one instrumentation library SHOULD be low.
Telemetry consumers that aggregate data from multiple instrumentation libraries and applications
should be prepared for `error.type` to have high cardinality at query time when no
additional filters are applied.

If the operation has completed successfully, instrumentations SHOULD NOT set `error.type`.

If a specific domain defines its own set of error identifiers (such as HTTP or gRPC status codes),
it's RECOMMENDED to:

- Use a domain-specific attribute
- Set `error.type` to capture all errors, regardless of whether they are defined within the domain-specific set or not.

**[2] `telemetry.sdk.component.id`:** The SDK MAY allow users to provide an id for the component instances. If no id is provided by the user,
the SDK SHOULD automatically assign an id. Because this attribute is used in metrics, the SDK MUST ensure a low cardinality in that case.
E.g. it MUST NOT use a UUID.
It instead MAY do that by using the following pattern as value: `<telemetry.sdk.processor/exporter.type>-<instance-counter>`:
Hereby, `<instance-counter>` is a monotonically increasing counter (starting with `0`), which is incremented every time an
instance of the given component type is created.
For example, the first Batch Span Processor will have `batch-span-0` as `telemetry.sdk.component.id`, the second one `batch-span-1` and so one.
These values will therefore be reused in the case of an application restart.

---

`error.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `_OTHER` | A fallback error value to be used when the instrumentation doesn't define a custom value. | ![Stable](https://img.shields.io/badge/-stable-lightgreen) |

---

`telemetry.sdk.processor.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `batch-span` | The builtin SDK Batching Span Processor | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `simple-span` | The builtin SDK Simple Span Processor | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `telemetry.sdk.span.exporter.spans_submitted`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.telemetry.sdk.span.exporter.spans_submitted -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `telemetry.sdk.span.exporter.spans_submitted` | Counter | `1` | The number of spans for which the `export` callback of the exporter has been invoked. This does not require the export of the span to have finished yet. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`telemetry.sdk.component.id`](/docs/attributes-registry/telemetry.md) | string | A name uniquely identifying the instance of the OpenTelemetry SDK component within its containing SDK instance. [1] | `batch-span-0`; `custom-name` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| [`telemetry.sdk.exporter.type`](/docs/attributes-registry/telemetry.md) | string | A name identifying the type of the OpenTelemetry SDK exporter. | `otlp-grpc`; `jaeger` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1] `telemetry.sdk.component.id`:** The SDK MAY allow users to provide an id for the component instances. If no id is provided by the user,
the SDK SHOULD automatically assign an id. Because this attribute is used in metrics, the SDK MUST ensure a low cardinality in that case.
E.g. it MUST NOT use a UUID.
It instead MAY do that by using the following pattern as value: `<telemetry.sdk.processor/exporter.type>-<instance-counter>`:
Hereby, `<instance-counter>` is a monotonically increasing counter (starting with `0`), which is incremented every time an
instance of the given component type is created.
For example, the first Batch Span Processor will have `batch-span-0` as `telemetry.sdk.component.id`, the second one `batch-span-1` and so one.
These values will therefore be reused in the case of an application restart.

---

`telemetry.sdk.exporter.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `otlp-grpc` | OTLP exporter over gRPC with protobuf serialization | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `otlp-http` | OTLP exporter over HTTP with protobuf serialization | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `otlp-http-json` | OTLP exporter over HTTP with JSON serialization | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `telemetry.sdk.span.exporter.spans_processed`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.telemetry.sdk.span.exporter.spans_processed -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `telemetry.sdk.span.exporter.spans_processed` | Counter | `1` | The number of spans for which the export has finished, either successful or failed [1] | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1]:** For successful exports, `error.type` must be empty. For failed exports, `error.type` must contain the failure cause.

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`error.type`](/docs/attributes-registry/error.md) | string | Describes a class of error the operation ended with. [1] | `timeout`; `java.net.UnknownHostException`; `server_certificate_invalid`; `500` | `Recommended` | ![Stable](https://img.shields.io/badge/-stable-lightgreen) |
| [`telemetry.sdk.component.id`](/docs/attributes-registry/telemetry.md) | string | A name uniquely identifying the instance of the OpenTelemetry SDK component within its containing SDK instance. [2] | `batch-span-0`; `custom-name` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| [`telemetry.sdk.exporter.type`](/docs/attributes-registry/telemetry.md) | string | A name identifying the type of the OpenTelemetry SDK exporter. | `otlp-grpc`; `jaeger` | `Recommended` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1] `error.type`:** The `error.type` SHOULD be predictable, and SHOULD have low cardinality.

When `error.type` is set to a type (e.g., an exception type), its
canonical class name identifying the type within the artifact SHOULD be used.

Instrumentations SHOULD document the list of errors they report.

The cardinality of `error.type` within one instrumentation library SHOULD be low.
Telemetry consumers that aggregate data from multiple instrumentation libraries and applications
should be prepared for `error.type` to have high cardinality at query time when no
additional filters are applied.

If the operation has completed successfully, instrumentations SHOULD NOT set `error.type`.

If a specific domain defines its own set of error identifiers (such as HTTP or gRPC status codes),
it's RECOMMENDED to:

- Use a domain-specific attribute
- Set `error.type` to capture all errors, regardless of whether they are defined within the domain-specific set or not.

**[2] `telemetry.sdk.component.id`:** The SDK MAY allow users to provide an id for the component instances. If no id is provided by the user,
the SDK SHOULD automatically assign an id. Because this attribute is used in metrics, the SDK MUST ensure a low cardinality in that case.
E.g. it MUST NOT use a UUID.
It instead MAY do that by using the following pattern as value: `<telemetry.sdk.processor/exporter.type>-<instance-counter>`:
Hereby, `<instance-counter>` is a monotonically increasing counter (starting with `0`), which is incremented every time an
instance of the given component type is created.
For example, the first Batch Span Processor will have `batch-span-0` as `telemetry.sdk.component.id`, the second one `batch-span-1` and so one.
These values will therefore be reused in the case of an application restart.

---

`error.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `_OTHER` | A fallback error value to be used when the instrumentation doesn't define a custom value. | ![Stable](https://img.shields.io/badge/-stable-lightgreen) |

---

`telemetry.sdk.exporter.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `otlp-grpc` | OTLP exporter over gRPC with protobuf serialization | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `otlp-http` | OTLP exporter over HTTP with protobuf serialization | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `otlp-http-json` | OTLP exporter over HTTP with JSON serialization | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

[DocumentStatus]: https://opentelemetry.io/docs/specs/otel/document-status
[MetricRecommended]: /docs/general/metric-requirement-level.md#recommended