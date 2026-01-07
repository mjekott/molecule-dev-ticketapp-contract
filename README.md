# Contracts

Protocol Buffer definitions and generated TypeScript code .

## Directory Structure

- `proto/` - Protocol Buffer definition files (.proto)
- `gen/` - Generated TypeScript files

## Generating TypeScript from Proto Files

To generate TypeScript files from the proto definitions, run:

```bash
protoc \
  --proto_path=./proto \
  --ts_proto_out=./gen \
  --ts_proto_opt=nestJs=true,package=omit \
  ./proto/*.proto
```

### Prerequisites

Make sure you have `ts-proto` installed globally:

```bash
npm install -g ts-proto
```

### Options

- `--proto_path=./proto` - Specifies the directory containing proto files
- `--ts_proto_out=./gen` - Output directory for generated TypeScript files
- `--ts_proto_opt` - ts-proto options:
  - `nestJs=true` - Generate NestJS-compatible code with decorators
  - `addGrpcMetadata=true` - Add gRPC metadata parameter to methods
  - `addNestjsRestParameter=true` - Add rest parameter for additional arguments
  - `outputServices=grpc-js` - Generate service definitions for @grpc/grpc-js
  - `useExactTypes=false` - Use simpler type definitions
- `./proto/*.proto` - Input proto files

### Using in NestJS

The generated code includes:

- `AuthServiceController` - Interface for your controller implementation
- `AuthServiceControllerMethods()` - Decorator to apply to your controller class
- `AuthServiceClient` - Interface for client-side usage
- `AuthServiceService` - gRPC service definition for module configuration
