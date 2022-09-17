public class Jump : MonoBehaviour
{
    
    public float jumpVelocity = 5f;

    // 更改重力達到長按 jump 跳更高
    public float fallMutiplier = 2.5f;
    public float lowJumpMutiplier = 2f;
    
    // 設定一個標籤，判定碰到即著陸
    [SerializeField] private LayerMask collisionMask;
    // 新增判定點 groundCheck 位置
    [SerializeField] private Transform groundCheck;
    [SerializeField] private float groundCheckRadius = 0.05f;
    [SerializeField]Rigidbody2D rb;
    void start(){

        rb = GetComponent<Rigidbody2D>();
        
    }


    void Update(){

        //Jump
        if(Input.GetButtonDown("Jump") && IsGrounded() ){
            // 
            rb.velocity = Vector2.up * jumpVelocity;
            
        }
        // BetterJump
        // 加速墜落感
        if(rb.velocity.y < 0){

            rb.velocity += Vector2.up * Physics2D.gravity.y * (fallMutiplier - 1) * Time.deltaTime;
        
        }
        // 若沒長按跳，則向上重力較小 = 加速向下
        else if(rb.velocity.y > 0 && !Input.GetButton("Jump")){

            rb.velocity += Vector2.up * Physics2D.gravity.y * (lowJumpMutiplier - 1) * Time.deltaTime;
        }
    }


    // 判定著地
    private bool IsGrounded(){

        return Physics2D.OverlapCircle(groundCheck.position,groundCheckRadius,collisionMask);

    }

}
