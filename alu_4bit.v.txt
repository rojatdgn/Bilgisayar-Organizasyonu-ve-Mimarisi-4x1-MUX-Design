module alu_4bit (
    input [3:0] A,
    input [3:0] B,
    input [1:0] ALU_Sel,
    output reg [3:0] Result,
    output reg CarryOut
);

    always @(*) begin
        CarryOut = 1'b0;
        
        case(ALU_Sel)
            2'b00: begin 
                {CarryOut, Result} = A + B; 
            end
            
            2'b01: begin 
                Result = A - B;
                CarryOut = (A < B);
            end
            
            2'b10: begin 
                Result = A & B;
            end
            
            2'b11: begin 
                Result = A | B;
            end
            
            default: Result = 4'b0000;
        endcase
    end

endmodule